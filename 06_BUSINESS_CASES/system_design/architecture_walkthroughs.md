# Four Architecture Walkthroughs

**Created:** 1 November 2026
**Status:** Fictional practice scenarios. Not Amber clients, projects or briefs.
**Purpose:** Practise one diagram, one write path and one failure for each case.

## 1. School: capture is not the same as attendance

```text
Teacher/guardian browser --HTTPS--> application --transaction--> SQL
                                          ^                    |
RFID gateway --device identity/event ID----+          audit + eligible reports
```

The browser and gateway are separate trust boundaries. A device can submit an event but cannot become a teacher or administrator. The application verifies device identity, payload shape, card mapping, eligible session and duplication before recording attendance. A teacher correction requires assignment scope and an audit reason. A guardian lookup requires a verified child relationship, including at export/download time.

**Normal path:** receive → validate/deduplicate → resolve eligible student/session → persist attendance/provenance → commit → acknowledge. If acceptance means only durable enqueueing, return pending explicitly instead of claiming the attendance is final.

**Failure trace:** the gateway loses the acknowledgement and sends the event again. The stable device/event key returns the durable result without a second business effect. If the period was closed before a late event arrived, it enters a review path instead of silently rewriting a released report.

**NFR decisions:** agree the required freshness and recovery time; measure at expected peak load; minimise child data in logs. Use a restore-tested backup, not merely a second database replica. Adopt an existing school package if its verified workflow fit is better than custom development.

**Explain aloud:** What if two scans have different event IDs? Attendance still has a student/session uniqueness rule. What if the card is shared? A scan does not prove identity; policy and exception handling remain necessary.

## 2. Inventory/POS: local atomicity, remote uncertainty

```text
POS/admin -> order module -> SQL: order/reservation/ledger/idempotency
                  |
             payment adapter <---- signed callback ---- provider
                  |
             reconciliation worker / exception queue
```

Keep the initial application modular but deployable as one unit. A separate job process is justified for retries or exports without creating a service per table.

**Normal path:** authorize warehouse/action → validate price/quantity → short guarded reservation transaction → payment attempt with stable provider key → confirmed payment transition → fulfilment. Avoid holding stock-row locks through a remote provider call. Reservation expiry and payment success racing need an explicit transition policy and reconciliation, not a timer that blindly deletes records.

**Failure trace:** provider accepts payment but the API response times out. State becomes unknown/pending, and the worker queries the same provider reference. Do not issue a fresh charge with a new ID. Deduplicate callbacks and verify amount/currency before applying paid state.

**Offline trade-off:** unrestricted disconnected sales from shared stock cannot guarantee no oversell. Choose online confirmation, allocated offline quotas or provisional orders with an explicit rejection/refund policy. Caching does not solve coordination.

**First tests:** simultaneous final-unit reservations; one key/different payload; callback before response; expired reservation followed by late success; transfer dispatch without receipt. Check ledger/balance agreement, not only HTTP success.

## 3. Reporting: publish a consistent and honest snapshot

```text
Read-only adapters -> raw input/run log -> validate/map -> reporting snapshot
                                                               ^
Client browser -> API -> verified tenant scope -----------------+
                         private exports + tenant-scoped cache
```

Separate source extraction from presentation. A source record needs provenance, a stable identifier/version and a tenant association. Define KPI owner, formula, period, currency, exclusions and version before chart selection. Read-only source credentials must not reach a browser bundle.

**Normal path:** create run → retrieve bounded pages → validate/deduplicate → reconcile totals → publish complete snapshot → advance watermark. For late updates, use supported change capture or a documented lookback/reconciliation strategy, not just the largest timestamp seen.

**Failure trace:** two sources succeed and the third fails. Keep the last complete snapshot with a freshness warning if consistency is required. If partial reporting is allowed, label the missing source prominently. Missing is not zero. A cache key includes tenant, filters, period and relevant report version; downloads recheck permission.

**First tests:** overlapping IDs across tenants; revoked membership; source deletes; duplicate pages after retry; KPI version change; mixed currencies; exporting a report created before permission revocation.

**Scale trigger:** measure slow query plans and report sizes before adding a separate warehouse or stream platform. A daily business decision does not automatically need subsecond ingestion.

## 4. Legacy integration: one authority per fact

```text
Customer -> portal -> SQL: request + outbox
                               |
                          adapter worker -> supported ERP API
                               ^                    |
                          inbox/dedupe <--- webhook/polling
                               |
                      portal read model + reconciliation
```

Agree which system owns customer identity, price, accepted order and fulfilment state. The portal's submitted request is not automatically an ERP-accepted order. Do not write into unsupported vendor tables because an API is inconvenient.

**Normal path:** authenticate customer mapping → store request/outbox atomically → adapter sends stable external ID → ERP accepts/rejects → update portal view. The outbox removes the local database-versus-publication gap; it does not create universal exactly-once delivery. Receiving handlers must deduplicate too.

**Failure trace:** worker crashes after ERP acceptance, before local acknowledgement. It looks up or retries the same external ID using the vendor's supported semantics. If the ERP cannot identify duplicates, send the uncertain item to a human-owned reconciliation workflow, not an unbounded creation retry loop.

**Cutover:** sandbox contract test → read-only shadow reconciliation → one-customer order pilot → confirm failure/recovery support → expand. Reverting the portal cannot automatically retract orders already accepted by the ERP.

## 5. One-page decision checklist

| Question | A good answer contains |
|---|---|
| Where is the business invariant enforced? | Constraint/guard/transaction plus business validation |
| What happens after a timeout? | Visible pending state and supported retry/reconciliation |
| Who may access this object? | Identity + action + object relationship, server-side |
| What if a dependency is down? | Defined degraded state, backoff and owner |
| What is actually needed for the pilot? | Small end-to-end slice and exclusions |
| What would change the architecture? | Measured volume, freshness, ownership or team constraint |

For each case, finish with one next validation and one cost of your recommendation. Compare your answer with the [worked evaluation](../solution_evaluations/worked_evaluation.md), not a fictional employer pass mark.
