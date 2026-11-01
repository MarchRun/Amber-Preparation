# Question Bank Schema

**Purpose:** Enforce identical metadata across all 120 questions so the bank can be filtered, rehearsed, and scored.
**Created:** 31 October 2026

---

## Required fields per question

Every item must use this exact structure. Do not omit a field. If a field does not apply, write `N/A` with a reason.

```markdown
### Q-<CAT>-<NN> — <Short title>

| Field | Value |
|---|---|
| **Category** | <one of the eight categories> |
| **Sub-skill** | <e.g. motivation, joins, complexity, conflict> |
| **Difficulty** | Foundation / Intermediate / Advanced |
| **Asked in** | <likely stage: HR screen / technical / business case / any> |
| **Question (EN)** | <one clear question, spoken register> |
| **Pertanyaan (ID)** | <natural Indonesian translation, not word-for-word> |
| **What is assessed** | <one sentence> |
| **Evidence basis** | <CV/portfolio fact, company fact, or "general knowledge"> |
| **Strong answer outline** | <3–5 bullets> |
| **Model answer (EN)** | <60–120 words, first person, grounded> |
| **Contoh jawaban (ID)** | <meaning-equivalent Indonesian, normally 50–120 words; do not pad a naturally shorter translation> |
| **Follow-up** | <one probing question the interviewer may ask next> |
| **Weak answer / red flag** | <what would damage credibility> |
| **Scoring anchor** | 1 = <weak> · 3 = <acceptable> · 5 = <strong> |
```

---

## Conventions

### IDs
- `INT-01` … `INT-15` — introduction and motivation
- `MOT-01` … `MOT-15` — company and role fit
- `CV-01` … `CV-10` — CV and project deep dive
- `FUND-01` … `FUND-20` — programming fundamentals
- `SQL-01` … `SQL-15` — SQL and databases
- `SE-01` … `SE-15` — software engineering
- `BEH-01` … `BEH-15` — behavioural and situational
- `CASE-01` … `CASE-15` — business case and problem solving

### Language
- English question is the primary wording. It should sound like something a real interviewer would say, not a textbook prompt.
- Indonesian is a meaning-equivalent translation for preparation, not a literal calque.
- Model answers should be speakable in roughly 45–75 seconds, verified by actual recording. Honest incident-completion prompts are allowed where no personal event is evidenced. No bullet-point answers in the spoken text.
- Avoid idioms that are hard to pronounce. Prefer short sentences.

### Grounding
- Candidate answers may only use facts in `../sources/candidate_fact_sheet.md`.
- No invented metrics, users, clients, team sizes, or outcomes.
- When a question asks about a technology Marchel has not used, the model answer must follow: **honest gap → closest transferable experience → concrete learning plan**.
- Company answers may only use facts in `../02_COMPANY_INTELLIGENCE/*`; Amber's internal assessment format and cut-off remain `UNKNOWN`.

### Difficulty
- **Foundation:** should be answerable by any informatics graduate; tests clarity.
- **Intermediate:** requires a concrete example, trade-off, or multi-step explanation.
- **Advanced:** requires judgement under ambiguity, system thinking, or defending a decision.

### Scoring anchor
Write all three levels explicitly. Example:
`1 = claims expertise without evidence · 3 = correct but generic · 5 = specific, honest, and tied to a real project`

---

## Answer length targets

| Difficulty | Spoken target | Written model |
|---|---:|---:|
| Foundation | 30–45 s | 50–80 words |
| Intermediate | 45–75 s | 70–110 words |
| Advanced | 60–90 s | 90–130 words |

---

## Quality checks before a category file is accepted

- [ ] Exact question count for the category.
- [ ] Unique IDs, sequential with no gaps.
- [ ] Every field present in every item.
- [ ] English and Indonesian versions convey the same question.
- [ ] No invented candidate facts.
- [ ] At least one follow-up per item.
- [ ] No answer claims Java, .NET, Angular, or Flutter project experience.
- [ ] No claim about Amber's rubric, cut-off, clients, or internal projects.
- [ ] Weak-answer field is specific, not "bad answer."
