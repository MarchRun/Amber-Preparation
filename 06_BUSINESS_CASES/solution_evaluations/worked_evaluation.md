# Worked Evaluation — Diagnose Before You Score

**Created:** 1 November 2026
**Status:** Entirely fictional teaching example. Not Marchel's answer, an Amber case or an observed assessment.

## 1. Deliberately weak proposal

> I will build a Next.js POS with a stock table. The page will read the current quantity and subtract the order amount. Hiding the manager menu protects adjustments. Cashiers can sell offline using cached quantity; all devices sync later, so overselling is impossible. On a payment timeout I will send a new charge. Reports will sum balances joined to all order lines. I will use microservices from the start because they scale better.

## 2. Findings grounded in the artifact

| Finding | Why it matters | Minimum correction |
|---|---|---|
| Read-then-write quantity | Concurrent buyers can both see the last unit | Guarded update/row lock plus transactional order and ledger |
| Menu-only access control | Direct API requests bypass UI visibility | Server-side action and warehouse/object authorization |
| Offline guarantee | Disconnected counters lack current shared-stock state | Online confirmation, quotas or explicitly provisional sales |
| New charge after timeout | Original payment may already have succeeded | Same stable key, lookup and reconciliation |
| Joining independent details | A balance repeats for each line, inflating totals | Define grain and aggregate separate facts before joining |
| Unjustified microservices | Adds network/operational costs without a given need | Start modular; identify a real separation trigger |
| No discovery or acceptance | No evidence the proposed features solve the client's priority | Clarify outcome, workflow, volume, constraints and pilot checks |

These are design defects, not claims about the real candidate. Each finding identifies the consequence and a concrete repair.

## 3. Illustrative scoring, not measured candidate performance

| Dimension | Example score /5 | Observable reason |
|---|---:|---|
| Clarification | 1 | No questions or declared assumptions |
| Structure | 2 | Recognisable POS proposal, but no coherent workflow/acceptance |
| Technical soundness | 1 | Races, duplicate charges and incorrect aggregation |
| Trade-offs | 1 | Universal claims instead of cost comparison |
| Communication | 3 | Understandable wording, despite incorrect content |
| Practicality | 1 | Unbounded offline promise and unnecessary decomposition |
| Honesty about assumptions | 1 | Presents impossible/unsupported guarantees as facts |

Total 10/35 describes only this invented paragraph under the local rubric. It is not a provider percentile, Amber threshold or candidate score. The critical safety defects require repair regardless of total.

## 4. Better proposed answer

> Before designing, I would clarify the definition of available stock, whether offline sales may be provisional, and which system owns payments and accounting. For a first release I recommend one modular application and a relational database, covering receiving, reservations, sales, adjustments and reconciliation.
>
> Stock availability would be protected by a guarded update or row lock inside a short order transaction, with matching history. Warehouse and adjustment permissions would be checked on the server. I would not hold database locks during a payment-provider request.
>
> A timeout leaves payment state unknown. I would use stable provider identifiers, verify callbacks and reconcile the original request before any new charge. For offline counters, the business must choose quotas, online confirmation or provisional orders; unrestricted offline use cannot guarantee shared-stock consistency.
>
> Reports would use an agreed grain and separate aggregation to avoid multiplied totals. I would pilot one warehouse and test a last-unit race, duplicate callback, unauthorised adjustment and restore/reconciliation path. I would expand only after staff accept the reconciled balances.

## 5. Why the revised answer is better—and still incomplete

It states questions, chooses a feasible slice, protects invariants, rejects false guarantees and gives concrete tests. It does not prove actual implementation performance. Missing details include order/payment transition rules, returns, opening balances, ownership of exceptions and real volume. A strong response would acknowledge those and prioritise the next question rather than claim perfection.

**Practice:** Hide section 4. Give a 90-second repair of the weak proposal. Then explain one unresolved risk and the evidence you would seek. Use the same method for the school, reporting and ERP cases.
