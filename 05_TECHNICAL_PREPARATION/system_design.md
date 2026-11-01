# Junior System Design

**Purpose:** Produce a clear design sized to the stated problem.
**Created / last updated:** 31 October 2026
**Status:** Fictional practice designs, not descriptions of Marchel's implementations or Amber systems.

## 1. Six steps

1. Clarify users, workflow, outcome, volume and constraints.
2. Restate scope, assumptions and what is out of scope.
3. Identify entities, invariants and trust boundaries.
4. Draw components, data flow, API and one critical write transaction.
5. Explain security, failures, tests and trade-offs.
6. Summarise delivery slice and validation questions.

Start with a modular application and relational database for a modest transactional system. Services add deployment, network, tracing and consistency costs; do not introduce them just to sound experienced.

## 2. Vocabulary with limits

Cache improves repeated reads but creates invalidation and staleness decisions. Queue decouples slow work and supports retries; handlers must tolerate duplicate delivery. Load balancer distributes traffic but does not fix database bottlenecks. Replication helps some availability/read workloads but is not backup. Backups need restore tests and recovery objectives.

CAP concerns behaviour during a network partition in a distributed system, not a universal "pick any two" feature menu. SQL/NoSQL selection depends on data/access/integrity needs, not a claim that one always scales better. Observability needs useful logs, metrics and traces with correlation IDs and restricted personal data.

## 3. Design A — School attendance

**Assumed scope:** students, mentors, admins; scheduled sessions; RFID import; corrections and reports. Hardware development and payroll excluded.

```text
Browser ----HTTPS----> Application/API ----> PostgreSQL
RFID gateway --device authentication--^       |
                                   report/job worker
```

Entities: user, role, student, class, enrollment, session, attendance, device_event, correction_audit. Attendance unique on `(student_id,session_id)`; device event unique on `(device_id,event_id)`. Store timestamps with timezone; define school-local reporting date. Preserve unknown-card events in a restricted exception queue, not as invented students.

Endpoints: `GET /sessions/{id}/attendance`, `POST /device-events`, `PATCH /attendance/{id}`, `GET /classes/{id}/reports?term=...`. Device identity cannot act as an admin; verify active card mapping, permitted device/location and session. Mentor access is limited to assigned classes, enforced server-side.

Critical flow: validate event → deduplicate → map student/session → upsert valid attendance → commit → acknowledge. An acknowledgement follows durable processing or durable enqueueing with explicit pending state. Corrections need actor/reason and audit. A duplicate scan must not create duplicate attendance.

Failure: offline gateway buffers event IDs; retries are safe. A late event may require review if the reporting period is closed. Test duplicate scans, clock skew, revoked card, unassigned mentor, missing scheduled sessions and correction history.

Scaling: index session/class lookups first; paginate reports; background large exports. Do not claim exact throughput without measuring. SQL constraints protect integrity even if two requests race.

## 4. Design B — Small inventory/POS

```text
POS + admin UI --> one application --> SQL database
                      |                   |
                payment adapter      stock ledger + orders
                      |
                optional job worker for receipts
```

Entities: product, warehouse, balance, movement, order, order_line, payment_attempt, idempotency_record. Balance unique on product/warehouse; quantities and money have explicit units. Stock movements are append-only corrections rather than hidden edits.

`POST /orders`, `POST /orders/{id}/payments`, `GET /stock?warehouse=...`, `POST /stock-adjustments`. Check actor/location permission. Reserve/consume inventory inside a transaction using a conditional stock decrement and matching ledger entry. Lock rows in consistent order for multi-product orders.

Do not hold a database transaction across a payment-provider call. Create pending order/payment state, use provider idempotency, verify callback signatures and reconcile unknown outcomes. Separate physical inventory state from payment state. An offline sale can oversell a shared pool; either allocate offline quotas, require online confirmation or explicitly accept business risk.

Tests: last-item race, repeated payment callback, negative quantities, return/refund, warehouse transfer, stale price and provider timeout. Scale with indexes, batch reports and a queue when justified; strong consistency matters for stock deduction, eventual consistency can be acceptable for analytics.

## 5. Design C — Client reporting dashboard

```text
Source systems -> restricted ingestion -> raw/staging -> validated reporting tables
                                                          |
Browser -> authenticated API -> tenant authorization ------+
```

Entities: tenant, user_membership, source, ingestion_run, source_record, metric_definition, report_snapshot. Include tenant scope in relevant keys/queries. Use read-only source credentials; never expose source database credentials to the browser.

Endpoints: `GET /reports?as_of=...`, `GET /ingestion-runs/{id}`, `POST /exports`. Report includes definition, currency/unit, freshness and quality status. Tenant identity comes from verified membership, not a trusted query parameter alone.

Failure: a partial source outage must display stale/partial status, not silently report zeros. Preserve raw input, validate totals, quarantine malformed rows, replay by stable source IDs. Define watermark and late-update policy; refresh a consistent reporting snapshot rather than exposing half-loaded data.

Trade-off: scheduled batch is simplest when daily freshness suffices. Streaming adds operational cost and still needs reconciliation. A cache key must include tenant and filter scope; a shared key can leak client data.

Tests: cross-tenant access, missing source, changed KPI definition, duplicate records, timezone boundary, different currencies, export permission and deleted membership.

## 6. Five-minute explanation structure

40s problem/scope; 60s architecture/data; 60s critical workflow; 60s security/failures; 40s trade-off; 40s delivery/open questions. A readable diagram plus one defensible invariant beats ten technology logos.

**Recommended references (not newly retrieved):** https://c4model.com/ ; https://learn.microsoft.com/en-us/azure/architecture/ ; https://www.postgresql.org/docs/current/explicit-locking.html . Compiled 31 Oct 2026.
