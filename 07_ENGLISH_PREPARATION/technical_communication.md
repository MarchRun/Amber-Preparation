# Technical Communication

**Purpose:** Explain real scope and hypothetical reasoning without mixing them.
**Created / last updated:** 31 October 2026

## 1. Project explanation structure

Context → Problem → Constraints → Decision → Result → Limitation. Only context/roles/stacks and broad responsibilities are documented. Exact constraints, alternative decisions, outcome metrics and defects require Marchel's confirmation. If unknown, say "A design question I would examine is..." rather than fabricate history.

### SMB Suvanna Dipa — safe spoken core

"SMB Suvanna Dipa is a Sunday school administration web application. My role was full-stack developer. I used Next.js, TypeScript, PostgreSQL and Supabase, with Figma listed for design. The application supports student, mentor and admin requirements. I built and maintained operational features and integrated RFID attendance with the web application. That is the documented scope of my contribution. To explain a particular design decision, I would show the actual relevant code or schema. For a future improvement, I would examine duplicate scan handling and permission tests. Those are proposed review areas, not claims that the original system had a particular defect."

Add one verified workflow from memory to reach 90 seconds. Do not add invented tables, architecture layers or missing test coverage.

### Bappenas — safe spoken core

"I was a backend developer intern at Kementerian PPN/Bappenas from June to July 2025. I developed backend features for an internal government system using PHP, CodeIgniter and MySQL. The internship team had four members, and my portfolio describes a project manager, system analyst, frontend developer and my backend role. We used Agile development with Jira and GitLab. I coordinated with team members and cross-department stakeholders to align the work with institutional workflows and protocols. I can describe my backend responsibility, but I would not claim full architecture or production deployment ownership from that evidence."

The dates do not prove an exact number of weeks. Likewise GitLab use does not prove a particular code-review or pipeline policy.

## 2. Explain an artifact

| Artifact | Useful spoken structure | Example, explicitly proposed |
|---|---|---|
| Schema | Entity → relationship → key → invariant | "I would link attendance to student and session, unique per pair." |
| API | Actor → action → input → authorization → result → error | "An assigned mentor submits a correction with a reason; a stale version is rejected." |
| Bug | Expected → actual → reproduction → evidence → fix → regression | "In this practice scenario, two retries create duplicates; a stable key prevents the second effect." |
| Trade-off | Options → criterion → choice → cost → revisit | "Batch is enough for daily reporting; streaming would reduce latency but add operations." |

## 3. Unknown-stack answers

- **Java:** "I have no evidenced Java project. I can transfer OOP and typed-programming concepts, but I would need to learn Java syntax, libraries and the team's framework. I would start with a small tested API."
- **.NET:** "I have not used .NET in a documented project. HTTP, SQL and TypeScript typing give me a foundation. I would learn C# and ASP.NET Core through one reviewed CRUD task."
- **Angular:** "My documented frontend experience is React and Next.js. Do you mean AngularJS or modern Angular? I would need to learn the relevant framework's components and data-flow conventions."
- **Flutter:** "I have no documented Flutter application. UI composition and API use transfer, but I would need Dart, widgets and platform-specific practice."
- **Oracle/Odoo/Dynamics:** "I have not implemented an ERP. Relational data and workflow concepts transfer. I would first learn the assigned module and supported integration boundary with functional guidance."

Do not promise production readiness in a fixed week count.

## 4. Fifteen clarification and repair phrases

1. "Could you repeat the last part, please?"
2. "Could you say that a little more slowly?"
3. "By X, do you mean A or B?"
4. "Should I focus on design or working code?"
5. "May I confirm the expected input and output?"
6. "Is this an assumption I may make?"
7. "Let me check that I understood."
8. "May I take twenty seconds to organise my answer?"
9. "I will explain the main workflow first."
10. "Let me correct one detail."
11. "I said X; I meant Y."
12. "That is a proposed improvement, not something I already implemented."
13. "I do not know that platform yet."
14. "The closest relevant experience is..."
15. "Does that address the part you wanted me to explain?"

Use one repair then continue. Repeated apologies obscure the answer more than a short pause does.
