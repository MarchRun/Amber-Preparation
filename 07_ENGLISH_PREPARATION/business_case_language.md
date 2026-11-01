# Business-Case Language

**Purpose:** Forty sentence frames and a spoken presentation outline.
**Created / last updated:** 31 October 2026
**Status:** Original practice; not an employer script.

## 1. Forty frames

| # | Function | Sentence |
|---:|---|---|
| 1 | Clarify | What is the main business outcome? |
| 2 | Clarify | Who uses the system every day? |
| 3 | Clarify | Who approves a correction? |
| 4 | Clarify | Which workflow must work in the first release? |
| 5 | Clarify | What system owns this information today? |
| 6 | Clarify | How fresh must the report be? |
| 7 | Clarify | What happens when the connection is unavailable? |
| 8 | Clarify | What would make the pilot successful? |
| 9 | Restate | My understanding is that the main problem is... |
| 10 | Restate | The first version will cover... |
| 11 | Restate | I will leave this feature out for now because... |
| 12 | Confirm | Is that a fair summary? |
| 13 | Assume | The brief does not specify this, so I will assume... |
| 14 | Assume | If that assumption changes, I would revise... |
| 15 | Structure | I will cover workflow, data and risks. |
| 16 | Structure | Let me start with the critical write path. |
| 17 | Structure | The key invariant is... |
| 18 | Structure | This record belongs to... |
| 19 | Compare | There are two reasonable options. |
| 20 | Compare | The first is simpler to operate. |
| 21 | Compare | The second reduces latency but adds... |
| 22 | Decide | Given the constraint, I recommend... |
| 23 | Decide | The cost of that choice is... |
| 24 | Revisit | I would revisit it if... |
| 25 | Failure | A timeout does not tell us whether the write succeeded. |
| 26 | Failure | A repeated event must not create another record. |
| 27 | Security | I would check permission on the server for this object. |
| 28 | Security | The client cannot choose an arbitrary tenant. |
| 29 | Test | The first test I would run is... |
| 30 | Test | I would also test the empty and concurrent cases. |
| 31 | Disagree | I see the benefit. My concern is... |
| 32 | Disagree | Could we compare it against the stated constraint? |
| 33 | Adapt | With that new requirement, I would change... |
| 34 | Interruption | Certainly. The short answer is... |
| 35 | Repair | Let me correct the assumption behind that answer. |
| 36 | Time | With five minutes left, I will finish... |
| 37 | Unknown | I would need to confirm that with the system owner. |
| 38 | Honest gap | This is my proposal, not a system I have already built. |
| 39 | Close | The pilot should demonstrate... |
| 40 | Close | My next step would be to validate... |

## 2. Five-minute presentation practice

**Fictional setting:** a school wants reliable attendance. This is not a real client brief. Read aloud with a diagram; expand with one concrete example in each timed segment rather than adding memorised jargon.

**0:00–0:40 — problem and scope**

"My understanding is that the main problem is unreliable attendance records and slow reporting. I would confirm whether attendance is daily or per session. For this proposal I assume sessions are scheduled and teachers are assigned to classes. The first release covers roster, attendance, corrections and reports. Fees and admissions are out of scope."

**0:40–1:40 — architecture and model**

"I recommend one modular web application and a relational database. Students enroll in classes, classes have sessions, and attendance links a student to a session. That pair is unique. The database should reject duplicates even when two requests arrive together. I would separate the raw device event from the attendance decision, because a scan may be duplicated, late or unmapped."

Point to the diagram and illustrate a student/session pair before proceeding.

**1:40–2:40 — workflow and permissions**

"A mentor records or corrects attendance only for an assigned class. Each correction has a reason and audit history. A guardian can see only a verified linked child's released report. Those checks happen on the server. A hidden button is not enough. For an RFID event, the gateway is authenticated and the stable event ID is deduplicated before the system acknowledges successful processing."

Give one permitted correction and one rejected action.

**2:40–3:40 — failure and tests**

"If connectivity fails, the device can retain pending events and retry. Pending is not the same as recorded. A late event in a closed period needs an approval rule. The first tests are a duplicate event, a mentor from another class and a report with no attendance record. I would calculate rates from eligible scheduled sessions, not just the rows that happened to be recorded."

Explain why one missing record must not silently become zero.

**3:40–4:20 — trade-off**

"I would compare a configured school package with custom development before committing. For capture, a manual or QR pilot may be simpler than immediate hardware expansion. RFID can improve convenience but adds card and device support and does not prove identity by itself. The choice depends on the actual workflow and budget."

**4:20–5:00 — next steps**

"I would pilot one class, reconcile one week's records, check correction history and verify guardian access before expansion. The school should agree the acceptance criteria and retention policy. My next question is which existing source owns the student roster. This design remains a proposal until those assumptions are confirmed."
