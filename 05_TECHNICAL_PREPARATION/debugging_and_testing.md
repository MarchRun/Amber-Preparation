# Debugging and Testing

**Purpose:** Show a repeatable diagnosis, not random edits.
**Created / last updated:** 31 October 2026
**Status:** Hypothetical exercises. No scenario below is claimed as a real candidate incident.

## 1. Twenty-minute protocol

| Minutes | Action | Evidence |
|---|---|---|
| 0–3 | Define expected/actual behaviour and impact | Exact input, environment, version, timestamp |
| 3–6 | Reproduce minimally | One failing request/test, not a vague complaint |
| 6–10 | Trace boundaries and form ranked hypotheses | Request → handler → query → response |
| 10–14 | Test one hypothesis at a time | Observation that could disprove it |
| 14–17 | Make smallest safe fix | Root cause distinguished from mitigation |
| 17–20 | Regression and neighbouring tests; explain | Test result, remaining risk, next step |

If production is affected, mitigation and escalation may take priority over diagnosis. Preserve logs and state; do not expose credentials, tokens or children's records in debugging output. If time expires, report what is known, ruled out and next; do not announce an unverified fix.

## 2. Tools and reasoning

Logs explain discrete events; metrics show rates/latency/error trends; traces link spans across components. Correlation IDs connect one request. Check a deployed version and environment before rewriting code. Binary-search a large input or code change set when the failure is reproducible; do not bisect uncommitted user work destructively.

Common classes: off-by-one; null assumptions; stale state; timezone errors; race conditions; permission omissions; invalid external payload; missing migration; incorrect configuration; resource leaks; unbounded queries. A slow request is not automatically a database problem—measure network, handler, query count and rendering separately.

## 3. Test design

Equivalence partitions reduce many inputs to meaningful groups. Boundaries check min−1/min/min+1, empty/one/many, absent/null/valid. Add concurrency and retry tests for writes. Use mocks for external contracts where isolation helps; a mocked SQL call does not verify real constraints or isolation. Keep some integration tests on the actual engine.

Unit example: grade calculation rejects weights that do not total 100%. Integration example: duplicate attendance violates a unique key. E2E example: assigned mentor signs in, corrects a record and sees an audited report. Regression example: an unassigned mentor receives a refusal after a permission fix.

## 4. Eight scenarios

| Scenario | First hypotheses and isolating observation | Fix direction and regression |
|---|---|---|
| Duplicate RFID attendance | Gateway retry versus UI double-submit; compare event IDs and timestamps | Deduplicate device events plus unique attendance key; replay identical event twice |
| Report omits zero-attendance students | INNER JOIN or right-table WHERE filter; inspect intermediate row count | Start from enrollment/schedule, LEFT JOIN; student with no record still appears |
| User sees another client's export | Missing tenant check or cache scope; test same URL with two memberships | Authorize export at generation and download; tenant-scoped cache; cross-tenant test |
| Stock goes negative sporadically | Read-then-write race; parallel last-unit purchases | Atomic guarded update/locking and ledger transaction; exactly one succeeds |
| Login works locally only | Cookie secure/domain/SameSite, HTTPS proxy or wrong environment | Inspect browser network/cookie rejection reason; correct configuration; deployed smoke test |
| Attendance appears a day early | UTC/local conversion or date truncation | Define timezone and boundary explicitly; tests before/after local midnight |
| Page latency rises with record count | N+1, unindexed filter, huge payload; measure query count and plan | Set-based query, suitable index, pagination; representative-load regression |
| Memory grows after each request | Unbounded global cache/listener or expected warm-up | Heap snapshot/retained paths; bound cache/remove listener; repeated-load plateau check |

## 5. Talk while solving

"I can reproduce it with this input. I have two hypotheses. I will test the query filter first because it explains the missing rows. This observation rules out the frontend. The patch fixes the cause; I will also test a student with no attendance so it does not return."

Avoid "it works now" without a test. Distinguish a diagnosis from a guess. A confident explanation with no falsifiable observation is not evidence.

**Recommended references (not newly retrieved):** https://testing-library.com/docs/ ; https://playwright.dev/docs/intro ; https://opentelemetry.io/docs/ . Compiled 31 Oct 2026.
