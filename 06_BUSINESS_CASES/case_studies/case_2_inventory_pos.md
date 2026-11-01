# Case 2 — Inventory and POS

**Purpose:** Protect stock and payment integrity under retries and concurrency.
**Created:** 31 October 2026
**Last updated:** 1 November 2026 — canonical case-study location.
**Status:** Fictional practice scenario. Not an Amber client, project, or brief.

## 1. Candidate brief

An SME distributor operates four warehouses. Sales sometimes exceed available inventory, and staff reconcile manual counts in spreadsheets. Propose inventory/POS improvements. Connectivity is unreliable at some counters. Budget, transaction volume and payment provider are unknown. Produce a 45-minute case response before reading the worked answer.

## 2. Clarify and scope

Ask: Does "available" exclude reservations? Are goods serialised/batched? Who approves adjustments and warehouse transfers? Are offline sales allowed to risk overselling? How are returns, taxes and payments represented? Is there an existing accounting system of record?

Assume simple counted units for the pilot, one currency per order and no serial tracking. Confirm these assumptions before delivery. MVP: product/warehouse setup, opening balances, stock movements, online order/reservation, payment state, returns and reconciliation. Defer loyalty and advanced demand forecasting.

Success: every stock change traces to a movement, concurrent sales cannot consume the same final unit, and unknown payment outcomes are visible for reconciliation.

## 3. Architecture and data

```text
POS browser / admin -> application -> SQL database
                           |          orders, balances, ledger, audit
                      payment adapter
                           |
                    provider + signed callbacks
Optional worker: receipts, exports, reconciliation
```

| Entity | Core fields / invariant |
|---|---|
| product | SKU unique, unit, active status |
| warehouse | ID, address, operating status |
| stock_balance | product + warehouse unique; on_hand, reserved, version |
| stock_movement | signed quantity, reason, reference, actor; append-only |
| order / order_line | state, price snapshot, quantity, warehouse allocation |
| reservation | expiry and order reference; explicit release policy |
| payment_attempt | provider reference, amount/currency, state, idempotency key |
| transfer | source/destination and in-transit state |
| adjustment / audit | count evidence, approver, reason and history |

Available = on_hand − reserved, if that is the agreed policy. Transfers cannot instantly appear in both locations; represent dispatch and receipt. Returns may require inspection before becoming sellable.

## 4. Critical write path

`POST /orders` accepts an idempotency key and positive quantities. Validate actor, active products, warehouse permissions and price rules. Within a short transaction, reserve stock using a conditional update; write order, allocation and stock/reservation history; commit. Lock multiple stock rows in deterministic order. If any requested quantity is unavailable, rollback or explicitly implement an agreed partial-order policy.

```sql
-- Illustrative reservation; use inside the order transaction.
UPDATE stock_balance
SET reserved = reserved + :qty, version = version + 1
WHERE product_id = :product_id AND warehouse_id = :warehouse_id
  AND :qty > 0 AND on_hand - reserved >= :qty;
-- Zero affected rows => reject/unavailable; do not continue as success.
```

Do not hold database locks while calling a payment provider. Use order states pending/reserved/paid/fulfilled/cancelled and separate payment states pending/succeeded/failed/unknown. On a timeout, query/reconcile the provider using the same payment key rather than issuing another charge. Verify callback signature, amount, currency and expected order; deduplicate callbacks. Release expired reservations with an auditable, retry-safe operation.

Endpoints: `GET /stock?warehouse=...`, `POST /orders`, `POST /orders/{id}/payment-attempts`, `POST /stock-adjustments`, `POST /transfers`, `POST /transfers/{id}/receive`. Enforce object-level authorization. Admin stock correction is a ledger movement, not a hidden overwrite.

## 5. Offline choice and reorder rule

An offline POS cannot guarantee global stock consistency with online sales without additional allocation rules. Choose online confirmation for shared-stock sales in the pilot. Alternatives: allocate a dedicated per-counter offline quota, or accept provisional orders subject to later rejection. Make the customer-facing consequence explicit.

Reorder point = expected demand during replenishment lead time + safety stock. Both depend on real history and supplier variability. Do not invent a universal threshold. Alert on available stock versus reorder point, excluding unusable/damaged inventory where appropriate.

## 6. Trade-offs, risks, tests

| Decision | Recommendation | Cost |
|---|---|---|
| Mutable quantity only vs ledger + balance | Ledger with transactional balance projection | More storage and reconciliation logic |
| Online consistency vs unrestricted offline | Online confirmation, later evaluate quotas | Some offline sales delayed |
| Build vs existing inventory package | Evaluate package workflows/integrations first | Licensing/configuration vs custom maintenance |

Main risks: inaccurate opening count, untracked adjustments, duplicate callbacks, delayed reservation release and warehouse permission leaks. Detect with ledger/balance reconciliation, payment exception queue and aging-reservation reports. A ledger is not magically trustworthy if people bypass it; restrict write access and audit adjustments.

Tests: two requests for one remaining item; one rejection; replay same order key with identical body; reject same key/different body; callback before response; provider timeout then success; refund after return; dispatch/receive transfer; expired reservation; negative/zero quantity; concurrent count adjustment. Recovery requires reconciling provider and stock records after restore, not just restarting the server.

## 7. Delivery and spoken walkthrough

Sequence: reconcile one warehouse opening count → import products → implement receipt/adjustment ledger → online order/reservation → payment reconciliation → transfers/returns → expand warehouses. Parallel-run key reports until staff accept the balances. Agree support ownership and backup restore checks before rollout.

Five-minute presentation cues:

1. "The outcome is trustworthy available stock and traceable payment state. I need to clarify reservations and the offline policy first."
2. "I propose one application with a SQL database. A ledger explains every change, while a balance supports fast stock checks."
3. "The last-unit race is prevented by an atomic guarded reservation in the order transaction, not by reading quantity and hoping it stays the same."
4. "Payments run outside that lock. Timeouts become unknown states that we reconcile using stable keys."
5. "For the pilot I require online confirmation for shared stock. Dedicated offline quotas are an alternative, with operational cost."
6. "I would demonstrate a last-unit concurrency test, duplicate callback test and transfer reconciliation before adding more counters."

Spend roughly 40–60 seconds on each cue with the diagram and one worked failure. This is proposed inventory reasoning, not a claim that Marchel built a POS.
