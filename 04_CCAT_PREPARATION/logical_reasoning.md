# Logical Reasoning

**Purpose:** Handle deductive, conditional, ordering, and set-based items quickly.
**Created:** 31 October 2026
**Last updated:** 31 October 2026
**Relevant CCAT weight:** ~10–20% (embedded in math/logic)
**Cross-references:** `verbal_reasoning.md`, `numerical_reasoning.md`

---

## 1. What is tested

Logical reasoning on the CCAT is not a separate official section; it appears inside math and logic and some verbal items.

Formats:
- Syllogisms
- Conditional statements (if/then, only if, unless)
- Ordering and arrangement
- Set problems (Venn diagrams)
- Deduction from rules
- Number/letter series with a logical rule
- True/false/undetermined judgments

---

## 2. Syllogisms

### Set translation
| Statement | Diagram |
|---|---|
| All A are B | A inside B |
| No A are B | A and B disjoint |
| Some A are B | A and B overlap |
| Some A are not B | Part of A outside B |

### Valid conclusions
- All A are B; all B are C → All A are C.
- All A are B; X is A → X is B.
- No A are B; X is A → X is not B.
- Some A are B → Some B are A.
- All A are B; some C are A → Some C are B.
- No A are B; all C are A → No C are B.

### Invalid conclusions
- Some A are B; some B are C → Some A are C. ❌
- All A are B; all C are B → All A are C. ❌
- No A are B; no C are B → No A are C. ❌
- All A are B; some B are C → Some A are C. ❌

**Rule:** "Some A are B" is reversible; "Some A are not B" is not generally reversible. "All" statements are not reversible and do not establish that a set is non-empty.

---

## 3. Conditional logic

### Forms
- **If P, then Q.** P is sufficient for Q. Q is necessary for P.
- **Only if Q, P.** Q is necessary for P. (Equivalent to "If P, then Q.")
- **P unless Q.** If not Q, then P. (Equivalent to "If not Q, then P.")
- **P if and only if Q.** P and Q are equivalent.

### Valid inferences
| Premise | Conclusion | Name |
|---|---|---|
| P → Q; P | Q | Modus ponens |
| P → Q; not Q | not P | Modus tollens |
| P → Q; Q | Nothing | Affirming the consequent (invalid) |
| P → Q; not P | Nothing | Denying the antecedent (invalid) |

### Common trap
"If it rains, the ground is wet. The ground is wet." Does it follow that it rained? No. Something else could have made it wet.

---

## 4. Ordering and arrangement

### Method
1. Draw slots or a line.
2. Place fixed items first.
3. Use relative clues ("A is left of B").
4. Mark "not" constraints.
5. Test options against all constraints.
6. If multiple arrangements are possible, the question usually asks what *must* be true.

### Example
Five people sit in a row: A, B, C, D, E.
- A is left of B.
- C is right of B.
- D is left of A.
- E is between B and C.

One valid order: D, A, B, E, C.

Do not assume uniqueness unless the constraints force it.

---

## 5. Set problems

### Two-set formula
|A ∪ B| = |A| + |B| − |A ∩ B|

### Neither
Neither = Total − |A ∪ B|

### Example
40 students; 25 take math; 20 take physics; 10 take both.
- Union = 25 + 20 − 10 = 35.
- Neither = 40 − 35 = 5.

### Three-set formula
|A ∪ B ∪ C| = |A| + |B| + |C| − |A∩B| − |A∩C| − |B∩C| + |A∩B∩C|

Use a Venn diagram for three sets; do not rely on memory alone.

---

## 6. Letter and symbol series

### Common patterns
- Alphabet position: A=1, B=2, ..., Z=26.
- Skip patterns: +2, +3, +4...
- Alternating sequences.
- Reverse alphabet.
- Vowel/consonant patterns.
- Letter pairs (AB, CD, EF...).

### Example
A, C, F, J, O, ?
Positions: 1, 3, 6, 10, 15 → differences +2, +3, +4, +5 → next +6 = 21 = U.

---

## 7. Worked examples

### L-EX-01 — Syllogism
**Question:** All managers are employees. No employees are volunteers. What must be true?
A) Some managers are volunteers.
B) No managers are volunteers.
C) All volunteers are managers.
D) All employees are managers.
**Answer:** B.
**Why:** Managers are inside employees; employees are disjoint from volunteers; therefore managers are disjoint from volunteers. D reverses the subset relationship and is not guaranteed. Do not choose between two valid conclusions by calling one "stronger"; a single-answer item should have one valid option.

### L-EX-02 — Some
**Question:** Some cats are black. All black things absorb light. What must be true?
A) All cats absorb light.
B) Some cats absorb light.
C) No cats absorb light.
D) All black things are cats.
**Answer:** B.
**Why:** The black cats are a subset of black things, all of which absorb light.

### L-EX-03 — Conditional
**Question:** If a user is an admin, they can delete records. Maria can delete records. What follows?
A) Maria is an admin.
B) Maria is not an admin.
C) Nothing certain about Maria's role.
D) All admins are Maria.
**Answer:** C.
**Why:** Affirming the consequent is invalid. Other roles may also have delete permission.

### L-EX-04 — Only if
**Question:** Only if you register can you vote. You voted. What follows?
A) You registered.
B) You did not register.
C) Registration guarantees voting.
D) Nothing.
**Answer:** A.
**Why:** Registration is necessary for voting. Voting implies registration.

### L-EX-05 — Ordering
**Question:** D is before A. A is before B. C is after B. Which order is valid?
A) A, D, B, C
B) D, A, B, C
C) D, B, A, C
D) A, B, D, C
**Answer:** B.

### L-EX-06 — Set
**Question:** In a class of 40, 25 like tea, 20 like coffee, and 10 like both. How many like neither?
A) 5 B) 10 C) 15 D) 20
**Answer:** A) 5.
**Method:** 25+20−10=35; 40−35=5.

### L-EX-07 — Series
**Question:** 2, 6, 12, 20, 30, ?
A) 36 B) 40 C) 42 D) 44
**Answer:** C) 42.
**Method:** n(n+1): 1×2, 2×3, 3×4, 4×5, 5×6, 6×7.

### L-EX-08 — Invalid inference
**Question:** All developers use computers. Some students use computers. Which must be true?
A) Some students are developers.
B) All developers are students.
C) No students are developers.
D) None of the above.
**Answer:** D.
**Why:** The students who use computers may or may not be developers.

---

## 8. Practice drill (8 items, 5 minutes)

1. All roses are flowers. No flowers are stones. Therefore: A) Some roses are stones B) No roses are stones C) All stones are roses D) Some stones are flowers.
2. Some A are B. All B are C. Therefore: A) All A are C B) Some A are C C) No A are C D) Some C are not A.
3. If P then Q. Not P. Therefore: A) Not Q B) Q C) Nothing certain D) P.
4. P unless Q. Not Q. Therefore: A) P B) Not P C) Q D) Nothing.
5. A is taller than B. C is shorter than B. D is taller than A. Who is tallest? A) A B) B C) C D) D.
6. 30 students; 18 play football; 12 play basketball; 5 play both. How many play neither? A) 5 B) 6 C) 7 D) 8.
7. Series: 1, 4, 9, 16, 25, ? A) 30 B) 36 C) 42 D) 49.
8. "All invoices are documents. Some documents are urgent." Which must be true? A) Some invoices are urgent B) All urgent documents are invoices C) Some documents are invoices D) No invoices are urgent.

**Answers:** 1-B, 2-B, 3-C, 4-A, 5-D, 6-A (30−(18+12−5)=5), 7-B, 8-C.

---

## 9. Method summary

| Type | First move |
|---|---|
| Syllogism | Draw sets; check "all/some/no" |
| Conditional | Write P → Q; test modus ponens/tollens |
| Ordering | Draw slots; place fixed items |
| Set | Venn diagram or inclusion-exclusion |
| Series | Check differences, ratios, squares, primes |
| "Must be true" | Eliminate options that are merely possible |

---

## 10. Common mistakes

- Treating "some" as "some but not all."
- Reversing "all A are B" to "all B are A."
- Affirming the consequent.
- Confusing "only if" with "if."
- Assuming a unique arrangement when constraints allow several.
- Forgetting to subtract the intersection in set problems.
- Choosing a possible conclusion when the question asks for a necessary one.

---

## 11. Source anchors

- Criteria candidate guide: https://www.criteriacorp.com/candidates/ccat-prep
- Criteria Assessment Guide: https://www.criteriacorp.com/files/Criteria-AssessmentGuide-AssessmentTypes.pdf

Retrieved 31 October 2026. Practice items are original.
