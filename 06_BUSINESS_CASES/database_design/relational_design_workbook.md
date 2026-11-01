# Relational Design Workbook

**Created:** 1 November 2026
**Purpose:** Four exercises with worked reasoning, not blank design templates.
**Status:** Fictional practice. SQL targets PostgreSQL; reasoned review, not database-executed.

## 1. Start from facts and invariants

For each noun, ask whether it is an entity, an attribute or an event. A student is an entity; their name is an attribute; a scan is an event. Do not collapse an event into the business state it may cause. Several scans may correspond to one attendance record.

```text
class 1 ---- many class_session
student many ---- many class (through enrollment with dates)
student 1 ---- many attendance ---- 1 class_session
device 1 ---- many device_event ---- zero/one processed attendance decision
attendance 1 ---- many correction_audit
```

An attendance record references a student and session, with a unique pair. Enrollment eligibility depends on class and date and usually needs application/transaction logic beyond simple foreign keys. A foreign key to a student does not prove they were enrolled in that class at that time.

## 2. Exercise A — Choose keys

**Prompt:** A student can attend many sessions. A gateway retries events after disconnection. Which unique constraints prevent which duplicates?

**Worked solution:**

- `student(id)` identifies one student; a natural institutional identifier may also be unique within the institution.
- `class_session(id)` identifies a scheduled occurrence, not merely a reusable weekday.
- `attendance(student_id, session_id)` is unique: two different event IDs cannot create two attendance facts for the same eligible pair.
- `device_event(device_id, event_id)` is unique: retrying one event cannot repeat its processing effect.
- A surrogate attendance ID alone protects neither business duplicate.

If multi-tenant IDs overlap, include `tenant_id` in uniqueness and composite foreign keys. Reject an event with a reused ID and a different payload rather than silently treating it as the original. Do not trust a card to identify a person forever; active card mappings can change and historical events need a defined interpretation.

**Test:** Send the same event twice; send two distinct scans for the same student/session; concurrently submit a manual record. Expect at most one attendance fact, preserved event provenance and an explicit correction policy.

## 3. Exercise B — Report zero attendance correctly

**Prompt:** The report must show every eligible student, including students with no attendance records. Why is `present rows / recorded rows` unsafe?

**Worked solution:** The denominator comes from eligible scheduled sessions, not the subset captured successfully. Begin from enrollment joined to scheduled sessions, excluding cancellations and dates outside enrollment. LEFT JOIN attendance so missing records remain visible.

Illustrative query against the following **assumed** columns: `student(id,name)`, `enrollment(student_id,class_id,starts_on,ends_on)`, `class_session(id,class_id,starts_at,cancelled)`, `attendance(student_id,session_id,status)`.

```sql
WITH eligible AS (
 SELECT DISTINCT e.student_id, s.id AS session_id
 FROM enrollment e
 JOIN class_session s ON s.class_id=e.class_id
 WHERE NOT s.cancelled
   AND (s.starts_at AT TIME ZONE 'Asia/Jakarta')::date >= e.starts_on
   AND (e.ends_on IS NULL OR
        (s.starts_at AT TIME ZONE 'Asia/Jakarta')::date <= e.ends_on)
   AND s.starts_at >= TIMESTAMPTZ '2026-10-01 00:00:00+07'
   AND s.starts_at <  TIMESTAMPTZ '2026-11-01 00:00:00+07'
)
SELECT st.id, st.name,
 COUNT(el.session_id) AS eligible_sessions,
 COUNT(*) FILTER (WHERE a.status='present') AS present_sessions,
 COUNT(*) FILTER (WHERE el.session_id IS NOT NULL AND a.status IS NULL)
   AS missing_records,
 100.0 * COUNT(*) FILTER (WHERE a.status='present')
   / NULLIF(COUNT(el.session_id),0) AS attendance_pct
FROM student st
LEFT JOIN eligible el ON el.student_id=st.id
LEFT JOIN attendance a ON a.student_id=el.student_id
 AND a.session_id=el.session_id
GROUP BY st.id,st.name ORDER BY st.id;
```

Assume unique attendance pairs and one eligibility fact per pair. `DISTINCT` here prevents overlapping enrollment records from multiplying eligibility, but such overlaps should also be investigated as a data-quality problem. Students with no eligible session have a null rate, not an invented 0%. Policy may display "not applicable". This query counts present versus scheduled sessions; excused-leave denominator rules must be agreed before changing it.

**Hand test:** Sari has four eligible sessions: two present, one absent, one missing. Result: eligible 4, present 2, missing 1, rate 50%, not 66.7%. Ari has zero eligible sessions: rate is null. Budi joined for the final two sessions: use two, not all four.

## 4. Exercise C — Stock ledger and balance

**Prompt:** Is a stock ledger sufficient if its matching balance is updated later in a separate transaction?

**Worked solution:** Not for an authoritative synchronous available-stock check. The order/reservation, ledger and balance projection need an agreed consistency boundary. For a simple SQL design, change them together in one short transaction, using guarded stock updates or row locks. An asynchronous analytics projection can lag if labelled, but an authoritative stock check must not rely on an unacknowledged stale total.

```text
BEGIN
  claim order idempotency key; verify payload
  guard/lock stock rows in deterministic order
  reject insufficient available quantity
  write order + reservation + movement/history
  store completed local result
COMMIT
```

A movement reason records why stock changed. A transfer needs source dispatch and destination receipt, possibly in-transit state. Do not count the same goods as available at both warehouses. An adjustment is a new authorised movement, not an edit that erases the previous history.

**Hand test:** On-hand 10, reserved 3 gives available 7. Reserving 5 leaves available 2, not on-hand 5 unless physical issue has occurred. Use consistent business definitions.

## 5. Exercise D — Prevent multiplied totals

**Prompt:** A client has two source systems and three report subscriptions. Joining all detail rows then summing source balances gives a surprising total. What is wrong?

**Worked solution:** Independent one-to-many relationships multiply rows. Aggregate each fact at its intended grain first, then join summaries. State the grain in plain language: one row per tenant, currency and reporting period, for example. Do not use `SUM(DISTINCT amount)` as a general repair; legitimate records can share an amount.

If source A contributes 100 and source B contributes 100, the real total is 200. Three matching subscriptions make the naive joined sum 600. `SUM(DISTINCT amount)` returns 100, also wrong. Separate aggregation returns 200 without multiplying by subscriptions. Never sum different currencies without an agreed conversion rule.

## 6. Two-minute design explanation

"I would identify the fact grain before choosing columns. For attendance, the business fact is one student per session, while scans are separate events. I enforce both event deduplication and attendance uniqueness. For reporting I start from eligible scheduled sessions so missing records stay visible. The database protects references and uniqueness; the application still checks enrollment, permission and period rules. I would test concurrency and zero-record cases before calling the design reliable."
