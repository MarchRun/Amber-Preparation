# Business-Case Self-Assessment Rubric

**Purpose:** Turn rehearsal into observable improvements.
**Created:** 31 October 2026
**Last updated:** 1 November 2026 — canonical solution-evaluation location.
**Status:** Original practice rubric. NOT Amber's rubric, weights or hiring criteria.

| Criterion | 1 — weak | 3 — acceptable | 5 — strong |
|---|---|---|---|
| Clarification | Starts coding without checking goal | Asks relevant questions | Prioritises questions that change design; separates assumptions |
| Structure | Disconnected feature list | Logical scope and solution | Traceable problem → requirements → design → validation |
| Technical soundness | Broken keys/workflows or unsafe writes | Plausible model/API | Explicit invariants, concurrency, retries and failure paths |
| Trade-offs | Tool choice by fashion | Alternative mentioned | Chooses with a constraint, cost and revisit trigger |
| Communication | Rambling or unreadable artifact | Understandable with some gaps | Concise memo/diagram; answers follow-ups directly |
| Practicality | Unbounded scope or unsupported delivery promise | Feasible MVP | Right-sized design, dependencies and pilot acceptance |
| Honesty | Invents facts or personal experience | Labels some assumptions | Clearly separates known, assumed, proposed and unknown |

Score each 1–5; total /35 is a personal practice measure only. Any invented experience or serious authorization/data-integrity omission needs correction regardless of total. Do not average away a critical defect.

## Score sheet

| Date / case / format | Time used | Clarify | Structure | Technical | Trade-off | Communication | Practical | Honesty |
|---|---|---|---|---|---|---|---|---|
| Not yet attempted | — | — | — | — | — | — | — | — |

For written work: cite the missing section or incorrect rule. For spoken work: record the minute at which the explanation became unclear. A score without an observed example is not evidence.

## Timed attempt

5 minutes clarify; 3 restate; 15 design; 7 risk/test/trade-off; 10 prepare; 5 present. Review afterwards: one strength, one critical gap, one specific next drill. Re-attempt the failed skill before starting a new case.

Common failures: no scope; no authoritative data source; "missing" treated as zero; permission check only in UI; transaction without concurrency protection; queue without deduplication; technology list without data flow; false claims that the fictional case is Amber's real assessment.
