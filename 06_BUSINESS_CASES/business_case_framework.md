# Business-Case Framework

**Purpose:** Clarify → Restate → Decompose → Design → Trade-offs → Next steps.
**Created / last updated:** 31 October 2026
**Evidence status:** Practice method. Not Amber's scoring process.

## 1. Clarify what changes the design

Ask two or three high-value questions before proposing tools. Do not ask ten questions already answered by the brief.

| Area | Useful question | Why it changes a decision |
|---|---|---|
| Outcome | Which operational error matters most? | Sets MVP and acceptance tests |
| Users | Who creates, approves and reads records? | Defines permissions and workflows |
| Scope | Which workflow must work on day one? | Prevents an impossible first version |
| Existing system | What must remain the system of record? | Prevents conflicting ownership |
| Scale | Peak concurrent users and daily transactions? | Sizes architecture without guessing |
| Freshness | Does a report need live data or daily data? | Batch versus streaming |
| Failure | Is an offline transaction allowed to oversell? | Exposes a business trade-off |
| Privacy | Which data is sensitive and who may export it? | Trust boundaries and retention |
| Delivery | Deadline, team and integration access? | Feasibility and sequencing |
| Success | How will the pilot be accepted? | Concrete validation, not feature count |

If answers are unavailable: "For this exercise I will assume X. If that is wrong, Y changes." List facts, assumptions and questions separately.

## 2. Restate and decompose

"The goal is fewer duplicate attendance records, not a complete school ERP. The first version covers scheduled sessions and corrections. I will leave fees and admissions out. Is that scope correct?"

An issue tree should minimise overlap without forcing artificial categories:

```text
Reliable attendance
  Capture: device identity, card mapping, session selection
  Integrity: duplicates, late events, corrections, audit
  Access: student/guardian, assigned mentor, admin
  Reporting: schedule denominator, permissions, period close
  Operations: offline retry, monitoring, support, retention
```

Do not confuse outcomes (accurate records) with features (dashboard). Prioritise must/should/later with a reason. Every must-have should trace to a user action and a testable outcome.

## 3. Design in a useful order

1. Workflow and states, including rejection and cancellation.
2. Entities, relationships, unique keys and invariants.
3. Components and trust boundaries in a simple text diagram.
4. API contract, input validation and object-level authorization.
5. Critical write path: transaction, retry, concurrent request.
6. Reports/read paths: freshness, pagination, missing data.
7. Tests, monitoring, backup and recovery.
8. Delivery slice and unresolved decisions.

Start from a modular application and SQL database for a modest transactional case. Prefer existing platform functionality if it satisfies requirements. A configured package can beat bespoke software; compare total delivery/maintenance cost and fit.

## 4. Trade-offs require a decision

Use: **Option → benefit → cost → decision → condition for revisiting**.

Example: "Daily batch ingestion is simpler and sufficient for yesterday's financial report. It creates up to a day's latency. I choose batch for the pilot. I would revisit it if the client needs same-hour exception alerts."

Mention the main risk with its detection and response, not only "we will monitor". Example: duplicate processing is detected by a unique event key and mismatch counts; safe replay plus reconciliation resolves it.

## 5. Time budgets

| Step | 20 min | 45 min | 90 min |
|---|---:|---:|---:|
| Read/clarify | 2 | 5 | 10 |
| Restate/scope | 2 | 3 | 5 |
| Model/design/build | 8 | 15 | 40 |
| Risks/tests/trade-offs | 3 | 7 | 15 |
| Prepare output | 2 | 10 | 10 |
| Present | 3 | 5 | 10 |

If coding is required, first confirm language, allowed libraries and whether working code outweighs documentation. Produce a thin vertical slice rather than half of every feature.

## 6. One-page memo template

```text
Problem and success measure:
Known facts:
Assumptions / questions:
MVP / exclusions:
Users / permissions:
Workflow and states:
Architecture:
Entities and invariants:
API and critical transaction:
Alternative considered / decision / cost:
Top risks and detection:
Tests and acceptance:
Pilot sequence / next checkpoint:
```

**Five-minute presentation:** 40 seconds problem/scope; 60 architecture/data; 60 workflow; 60 security/failure/test; 40 decision/cost; 40 pilot and open question. Leave room for interruptions; answer the question rather than restarting your speech.

## 7. Language that makes reasoning visible

- "This is given in the brief; this is my assumption."
- "I would validate the denominator before showing this percentage."
- "This component is optional; I would not add it until volume justifies it."
- "The retry is safe because the same event key cannot create a second record."
- "I have not implemented that platform. This is a proposed design."
- "With ten minutes left, I will finish the critical workflow and list the rest."

## 8. If you remember only five things

1. Clarify the outcome before naming a stack.
2. State scope and assumptions explicitly.
3. Protect one critical business invariant.
4. Explain one failure path and one test.
5. Choose an option, admit its cost, and identify the next validation.
