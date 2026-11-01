# Programmer Business Case

**Purpose:** Prepare for an unknown-format business case without overfitting to one guess.
**Created:** 31 October 2026
**Last updated:** 31 October 2026
**Research status:** Amber's actual case format is not public
**Confidence:** Low for format; high for general evaluation criteria

---

## 1. What is confirmed

- The stage is called "Programmer Business Case."
- It is part of a 4.5-hour assessment alongside the CCAT.
- The company is an IT consultancy serving enterprise clients.
- The role advertisement emphasises programming fundamentals, SQL, research ability, common sense, and teamwork.

## 2. What is not confirmed

- Written, spoken, or coding format.
- Individual or group.
- Time limit.
- Language and tools allowed.
- Whether a presentation is required.
- Whether the case is based on a real Amber client (it may be fictionalised).

**Rule:** Prepare a transferable method, not a guessed script.

---

## 3. Plausible formats

| Format | What it looks like | What evaluators see | Preparation |
|---|---|---|---|
| A. Written case memo | Read a scenario, produce requirements/design in a document | Structure, completeness, clarity | Use the 6-step template |
| B. Live discussion | Interviewer describes a problem, asks how you'd solve it | Reasoning, questions, trade-offs | Practise thinking aloud |
| C. Coding task | Small program or bug fix in an IDE or shared editor | Correctness, code quality, testing | Practise arrays/strings/SQL |
| D. SQL task | Write queries against a schema | Joins, aggregation, edge cases | Drill SQL |
| E. System design whiteboard | Draw architecture and schema | Decomposition, data flow, NFRs | Use C4-lite diagrams |
| F. Presentation | Prepare slides and present | Communication, synthesis | 5-minute structure |
| G. Group case | Team discusses and presents | Collaboration, leadership | Role clarity, include others |
| H. Debugging exercise | Given broken code/logs, find and fix | Method, communication | Reproduce → isolate → fix → test |

**Most likely:** A + B, with a small technical component. The title "Business Case" suggests business analysis more than algorithms. But do not dismiss C/D.

---

## 4. What evaluators are likely scoring

| Criterion | Weight (guess) | Evidence they look for |
|---|---:|---|
| Requirement understanding | 20% | Clarifying questions; explicit assumptions |
| Structured problem solving | 20% | MECE decomposition; logical flow |
| Technical soundness | 20% | Correct data model, API, algorithm, SQL |
| Trade-off reasoning | 15% | Options compared; constraints acknowledged |
| Communication | 15% | Clear English; concise; answers questions |
| Practicality | 10% | Feasible for a junior/small team; avoids over-engineering |

These weights are a hypothesis, not Amber's rubric.

---

## 5. The six-step method

Use this for any case, written or spoken.

### Step 1 — Clarify (2–5 minutes)
Ask 3–6 questions covering:
- **Goal:** What business outcome matters?
- **Users:** Who uses it, and what roles?
- **Scope:** What is in/out for v1?
- **Volume:** How many users/records/transactions?
- **Constraints:** Deadline, budget, team, existing systems.
- **Compliance:** Personal data, audit, retention.
- **Success:** How will we measure it?

Do not ask questions you can answer from the prompt. Do not ask more than six.

### Step 2 — Restate (1 minute)
> "So the problem is X. The primary users are A and B. The key constraint is Y. For v1, I will focus on Z and leave W out. Is that correct?"

This confirms understanding and buys thinking time.

### Step 3 — Decompose (3–5 minutes)
Break into:
- Users and roles
- Core workflows
- Data entities
- Integrations
- Non-functional requirements
- Risks

Use a simple issue tree, not a fancy framework.

### Step 4 — Design (10–15 minutes)
Produce, in order:
1. Scope and assumptions
2. User stories / use cases
3. Data model (entities, relationships, keys)
4. API endpoints
5. Architecture (components, data flow)
6. Security and permissions
7. Testing strategy
8. Delivery plan

### Step 5 — Trade-offs (3–5 minutes)
Compare at least two options:
- Build vs. buy/configure
- Monolith vs. service
- SQL vs. NoSQL
- Sync vs. async
- Custom code vs. platform feature

State the decision, the reason, and what would change it.

### Step 6 — Present and next steps (3–5 minutes)
Summarise:
- Problem
- Recommended solution
- Why this option
- Risks/mitigations
- What I would do in the first two weeks
- Open questions

---

## 6. Answer template (written)

```markdown
# Case: [Name]

## 1. Understanding
- Business goal:
- Primary users:
- Scope for v1:
- Out of scope:
- Assumptions:

## 2. Requirements
### Functional
| ID | Requirement | Priority |
|---|---|---|
| FR-1 | ... | Must |

### Non-functional
- Performance:
- Availability:
- Security:
- Maintainability:
- Usability:

## 3. Solution
### Architecture
[text diagram]
### Data model
| Entity | Key fields | Relationships |
### API
| Method | Path | Purpose |
### Key logic
[pseudocode]

## 4. Trade-offs
| Option | Pros | Cons | Decision |
|---|---|---|---|

## 5. Risks
| Risk | Impact | Mitigation |
|---|---|---|

## 6. Testing
- Unit:
- Integration:
- E2E:
- Edge cases:

## 7. Delivery plan
- Week 1:
- Week 2:
- Later:

## 8. Open questions
- ...
```

---

## 7. Technical checklist by case type

### 7.1 Employee/student/patient management
- Entities: person, role, account, record, audit log.
- Auth: login, password hashing, session/JWT, role-based access.
- CRUD with validation and soft delete.
- Search, pagination, filtering.
- Reports and export.
- Privacy: least privilege, audit trail.

### 7.2 Inventory/order/POS
- Entities: product, stock movement, order, order line, payment, supplier.
- Concurrency: prevent overselling (transaction + row lock or optimistic version).
- Idempotency for payments and retries.
- Stock ledger rather than mutable quantity only.
- Reporting: reorder point, slow-moving stock.

### 7.3 CRM
- Entities: lead, account, contact, activity, opportunity.
- Pipeline stages and conversion.
- Duplicate detection.
- Permissions by team/region.
- Integration with email/calendar.

### 7.4 Finance/reconciliation
- Entities: transaction, source record, journal, mapping rule, exception.
- Idempotent ingestion; deduplication.
- Validation rules and exception queue.
- Audit trail; immutable ledger.
- Period close and lock.

### 7.5 Logistics/field operations
- Entities: shipment/job, stop, driver/inspector, proof, event.
- Offline-first sync; conflict resolution.
- Geolocation and photo evidence.
- Status machine and SLA tracking.

### 7.6 Learning/school
- Entities: student, guardian, class, enrollment, attendance, grade.
- Role separation: student, teacher, admin, guardian.
- Attendance and grade calculations.
- Term/semester boundaries.
- Report cards and audit.

---

## 8. SQL expectations

The ad explicitly warns against superficial SQL. Be ready to write:

```sql
-- Employees earning above their department average
SELECT e.name, e.salary, d.name AS department
FROM employees e
JOIN departments d ON d.id = e.department_id
WHERE e.salary > (
  SELECT AVG(e2.salary)
  FROM employees e2
  WHERE e2.department_id = e.department_id
);
```

```sql
-- Departments with more than 5 employees, highest average first
SELECT d.name, COUNT(*) AS headcount, AVG(e.salary) AS avg_salary
FROM employees e
JOIN departments d ON d.id = e.department_id
GROUP BY d.id, d.name
HAVING COUNT(*) > 5
ORDER BY avg_salary DESC;
```

Know:
- INNER vs. LEFT JOIN
- WHERE vs. HAVING
- GROUP BY rules
- Subqueries vs. CTEs
- Window functions (`ROW_NUMBER`, `RANK`, running totals)
- Indexes and when they help
- Transactions and isolation basics
- Normalization (1NF, 2NF, 3NF)
- Primary/foreign keys, unique constraints, null semantics

---

## 9. Coding expectations (if applicable)

Likely junior-level tasks:
- Reverse a string / check palindrome
- Count frequencies
- Find duplicates
- FizzBuzz-style logic
- Sum pairs / two-sum
- Flatten an array
- Parse and validate input
- Simple class design (e.g., parking lot, bank account)

What matters:
1. Clarify input/output and edge cases.
2. State the approach before coding.
3. Write readable code with meaningful names.
4. Handle empty/null/invalid input.
5. Test with examples, including edge cases.
6. State time/space complexity.

---

## 10. Common mistakes

| Mistake | Why it hurts | Fix |
|---|---|---|
| Jumping to code immediately | Signals poor requirement analysis | Clarify first |
| Over-engineering (microservices, Kafka for 100 users) | Signals poor judgment | Right-size the solution |
| Ignoring permissions | Enterprise clients care | Include roles and access control |
| No error handling | Real systems fail | Add validation and failure paths |
| No testing | Quality risk | Include a test plan |
| Vague trade-offs ("it depends") | No decision | Choose and justify |
| Too much jargon | Hides weak understanding | Explain simply |
| Not asking questions | Guessing | Ask 3–6 targeted questions |
| Running out of time silently | Incomplete deliverable | Narrate progress and prioritise |
| Defending a flawed design | Poor coachability | Adjust when challenged |

---

## 11. Time allocation

For a 45-minute case:

| Phase | Time |
|---|---:|
| Read and clarify | 5 min |
| Restate and scope | 3 min |
| Model and design | 15 min |
| Trade-offs and risks | 7 min |
| Prepare output | 10 min |
| Present | 5 min |

For a 20-minute case:
- 2 min clarify
- 2 min restate
- 10 min solve
- 6 min present

For a 90-minute case:
- 10 min clarify
- 10 min plan
- 45 min build/write
- 15 min test/review
- 10 min present

---

## 12. Spoken-case phrase bank

- "Before I design anything, may I clarify three things?"
- "My understanding is that the main goal is X, not Y. Is that right?"
- "I'll assume v1 handles A and B, and defer C. I'll note that as an assumption."
- "There are two reasonable options here. Option one is faster; option two is more flexible. I would choose one because..."
- "The main risk is data consistency during concurrent updates. I would mitigate it with a transaction and a unique constraint."
- "If I had more time, I would add X. For now, I would ship the thin end-to-end slice."
- "I don't have enough information to decide that. What I would do is check with the finance team."

---

## 13. Evaluation rubric (self-assessment)

Score each 1–5 after practice:

| Criterion | 1 | 3 | 5 |
|---|---|---|---|
| Clarification | None | Some relevant questions | Targeted, high-value questions |
| Structure | Rambling | Logical but uneven | Clear, MECE, signposted |
| Technical accuracy | Wrong | Mostly correct | Correct and precise |
| Trade-offs | Absent | Mentioned | Compared with criteria |
| Communication | Hard to follow | Understandable | Concise, confident, audience-aware |
| Practicality | Over-engineered | Feasible | Right-sized for constraints |

Target: 4+ average before assessment day.

---

## 14. Source anchors

- Amber Fresh Graduate Programmer ad: https://glints.com/id/en/opportunities/jobs/fresh-graduate-programmer/57dc25b6-6867-4088-bc74-01e7b157a967
- Amber Custom Development: https://www.ambersof.com/en/solutions/custom-development
- Amber Solutions: https://www.ambersof.com/en/solutions

Retrieved 31 October 2026.
