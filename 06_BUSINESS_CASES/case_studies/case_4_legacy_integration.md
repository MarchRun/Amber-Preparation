# Case 4 — Legacy ERP and Web Portal Integration

**Purpose:** Reason about ownership, retries, reconciliation and cutover.
**Created:** 31 October 2026
**Last updated:** 1 November 2026 — canonical case-study location.
**Status:** Fictional practice scenario. Not an Amber client, project, or brief.

## 1. Candidate brief

A manufacturer keeps customers and orders in a legacy ERP. A new customer portal must show status and submit new orders. Teams currently copy data manually. You do not know the ERP vendor, API availability or change limits. Produce a practical integration design in 45 minutes.

## 2. Questions and assumptions

Who owns customer master data and pricing? Can the ERP expose supported APIs or exports? What refresh delay is acceptable? How are customer IDs mapped? Are portal orders binding immediately or subject to ERP approval? What happens when the ERP is down? Can the same order arrive from another channel? Who owns support and reconciliation?

Assume ERP is authoritative for accepted orders, pricing and customer master; portal can submit an order request with a stable external ID. Do not assume direct writes into vendor tables are supported. The pilot includes order submission/status and customer display; exclude general bidirectional editing until ownership rules are agreed.

## 3. Pattern choice

| Pattern | Benefit | Cost / constraint |
|---|---|---|
| Supported synchronous API | Immediate validation | ERP latency/outage reaches portal; timeout ambiguity |
| Scheduled batch/export | Often feasible for legacy | Delay and late-change/reconciliation handling |
| Webhook | Pushes changes promptly | Delivery gaps, duplicates, authentication and replay |
| Durable queue + adapter | Decouples portal and ERP availability | Pending states, worker operation and retries |

Choose supported APIs where available. Use a durable submission queue if business accepts pending requests; use batch for status if APIs are absent and freshness permits. A queue does not remove the need for stable IDs and reconciliation. If there is no supported write interface, escalate vendor integration options rather than propose unsafe SQL writes.

## 4. Architecture and mapping

```text
Customer -> portal/API -> portal DB (request + outbox in one transaction)
                                      |
                                 adapter worker
                                      |
                               supported ERP interface
                                      |
                 status polling/webhooks -> inbox -> portal read model
```

Outbox publication can be retried. Downstream processing deduplicates; do not promise "exactly once" delivery across independent systems. Record `(source_system, external_id)` uniquely. Maintain portal-to-ERP IDs, mapping version and reconciliation state.

| Entity | Function |
|---|---|
| customer_mapping | Portal identity to ERP customer; approved relationship |
| order_request | External request ID, payload hash, state and actor |
| outbox_event | Durable work pending publication |
| inbox_event | Deduplicate incoming ERP notifications |
| integration_attempt | Time, response class, retry count, correlation ID |
| reconciliation_issue | Missing/mismatched record, owner, resolution |

Define field mapping: currency/unit conversion; product code mapping; decimal precision; local dates vs timestamps; required address fields; ERP enumerations; customer deactivation; tax/pricing authority. Reject unmapped products rather than substitute silently.

Endpoints: `POST /order-requests`, `GET /order-requests/{id}`, `GET /orders/{id}`, `GET /customers/me`. Verify customer membership/ownership server-side. A portal user cannot choose another ERP customer ID. Minimise personal data in transport logs.

## 5. Failure handling and invariants

Portal states: draft → submitted/pending → accepted or rejected; status updates may later show fulfilled/cancelled. "Submitted" is not "accepted". On API timeout, lookup the same external ID before retrying creation. If the ERP cannot deduplicate/look up external IDs, a manual uncertainty queue may be safer than automatic repeated creation.

Retry transient errors with bounded exponential backoff and jitter. Permanent validation errors need a correction workflow, not infinite retries. Rate limits need backpressure. A dead-letter/exception queue needs an owner and replay tooling. Verify signatures/credentials, expiry and replay protection on inbound events.

Reconcile counts, amounts and state per agreed period. Detect lost webhook updates by scheduled polling or supported change retrieval. A success response from the adapter is not proof that all records reconcile.

## 6. Cutover, tests and trade-offs

First map real workflows with functional staff. Test in vendor-supported sandbox using synthetic data. Backfill mappings and compare counts. Shadow status reads before portal writes. Pilot one customer group, avoid dual writers for the same field, agree fallback to existing ordering channel, and define the point at which duplicates must be manually reconciled. Backups do not automatically undo orders already sent to the ERP.

Tests: duplicate request key; same key/different payload; timeout after ERP acceptance; callback before response; out-of-order status; revoked customer; unmapped product; ERP outage; replay after worker restart; partial batch; currency precision. Contract tests must reflect the actual supported interface/version.

| Trade-off | Proposed choice | Explicit cost |
|---|---|---|
| Bidirectional everything vs single ownership | Field-level single authority | Some portal edits require a request/approval |
| Immediate confirmation vs resilient queue | Pending state if business accepts it | Customer waits for acceptance |
| Rewrite ERP vs adapter boundary | Adapter using supported contracts | Mapping/legacy limits remain |

Suggested delivery slices: read-only status → mapping reconciliation → sandbox order request → outage/retry verification → limited customer pilot → broader rollout. Timing depends on ERP access and approvals, which are unknown.

## 7. Five-minute spoken cues

"The first decision is ownership. I would confirm which system owns customer data, pricing and accepted orders, and which integration interfaces the ERP supports.

I propose an adapter boundary rather than direct table writes. The portal records a request and outbox event atomically; a worker submits it through the supported interface. The user sees pending until the ERP accepts it.

Each request has a stable external ID. After a timeout I query that ID rather than create a second order. Incoming status events are also deduplicated, and a reconciliation job catches missed updates.

I choose a queue only if delayed acceptance is acceptable. Otherwise we need an explicit synchronous failure policy. Neither option removes uncertainty; it makes the state visible.

I would test duplicate submission, timeout after acceptance, wrong customer access and ERP outage before a small pilot. The next dependency is access to the vendor's actual contract and a functional owner for mapping rules."

Show one timeout timeline and one mapping table to expand these cues to five minutes. Oracle, Odoo and Dynamics are general ERP examples only; no vendor is assumed for this case and no candidate ERP experience is implied.
