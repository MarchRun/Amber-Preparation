# Software Engineering

**Purpose:** Explain how a small team delivers safe changes.
**Created / last updated:** 31 October 2026

## 1. From need to delivery

Discover problem → agree requirements → design a thin solution → implement → verify → release → observe → improve. Waterfall emphasises staged planning; iterative approaches revisit decisions with feedback. Neither removes the need for requirements, testing or documentation.

A functional requirement describes behaviour: "A mentor records attendance for an assigned class." A non-functional requirement constrains quality: "Only authorised mentors may access their class records; agreed report response time is measured at an agreed load." Do not invent response-time targets as existing company requirements.

**User story:** As a mentor, I want to correct an attendance mistake so the term report is accurate.
**Acceptance criteria:** Given an assigned mentor and an open session, a valid correction records old/new status, actor, reason and time. An unassigned mentor is denied. A closed term requires an authorised override. Repeating the same request does not duplicate the correction event.

## 2. Agile and Scrum, accurately

Agile values feedback and adaptation; it is not "no documentation". Scrum uses a Product Owner, Scrum Master and Developers; events include Sprint Planning, Daily Scrum, Sprint Review and Retrospective. Product Backlog, Sprint Backlog and Increment are artifacts with commitments. A daily meeting is not proof a team uses full Scrum. The CV documents an Agile internship, not every Scrum event.

Estimate with assumptions, dependencies and uncertainty. Separate effort from elapsed time. State a range and a next checkpoint: "I would first inspect the existing report query; after that spike I can narrow the estimate." Raise a blocker with what you tried, impact and the specific decision needed.

## 3. Git to release

1. Read ticket and acceptance criteria; confirm unclear scope.
2. Create a small branch from the team's agreed base.
3. Implement one coherent change; add tests and migration notes.
4. Inspect diff, secrets, generated files and backward compatibility.
5. Open a review request: purpose, approach, test evidence, risks, screenshots if relevant.
6. Address review; merge using team policy; deploy via the authorised pipeline.
7. Verify behaviour and monitoring; keep a rollback/roll-forward plan.

Merge preserves divergent history with a merge commit when needed. Rebase replays commits onto a new base and changes commit IDs. Do not rewrite shared history without agreement. Commands are not the skill; understanding the diff and collaboration policy is.

**Review checklist:** correctness; authorization per object; validation; transaction boundaries; null/empty cases; tests; meaningful names; logging without secrets; query count; migration safety; accessibility if UI; useful documentation. Comment on impact and offer a concrete improvement, not personal taste as a law.

## 4. Quality, delivery and operation

Unit tests cover isolated logic; integration tests cover boundaries such as real database constraints; E2E checks user workflows. The pyramid is a cost/feedback heuristic, not a mandatory numerical ratio. Add a regression test for a bug at the cheapest level that would catch it.

CI validates changes automatically. Continuous delivery keeps releases ready with approval possible; continuous deployment automatically releases eligible changes. A green build does not prove user acceptance or safe data migration. Store secrets in controlled secret management, never in a repository or client bundle.

Useful documents: README/setup; API contract; schema/migration notes; decision record with alternatives; runbook with recovery steps. Technical debt is a trade-off with a future cost; track impact and revisit conditions, not just a vague complaint about old code.

Incident protocol: establish impact → mitigate safely → communicate owner/checkpoint → preserve evidence → fix root cause → verify recovery → blameless follow-up. Do not debug by making many untracked production changes. A rollback may not reverse a destructive migration.

## 5. Candidate evidence boundaries

| Topic | Documented evidence | Not yet proven |
|---|---|---|
| Team workflow | Four-person Agile Bappenas internship; Jira/GitLab | Exact branching/review/CI policy |
| Requirements | Institutional workflows; Simonika departmental SOPs | Sole analyst/architecture ownership |
| Planning | Kibang specifications, budget, risks, testing documentation | Professional engineering management |
| Deployment | Iterary cloud setup, automated workflow, traffic routing | Multi-region availability or any specific CI vendor |
| Quality | Testing documentation in Kibang portfolio | Automated coverage percentage or lack of a test suite |

Say "I would use this process" for proposed practice. Do not turn it into "we always did this" without a real example.

## 6. Oral rehearsal

Explain a ticket from requirement to release in 60 seconds. Then answer: What if the requirement changes halfway? What makes a review actionable? What would block deployment? What if the database migration cannot be rolled back? Which artifact proves acceptance?

**Recommended references (not newly retrieved):** https://agilemanifesto.org/ ; https://scrumguides.org/ ; https://git-scm.com/doc ; https://martinfowler.com/articles/practical-test-pyramid.html . Compiled 31 Oct 2026.
