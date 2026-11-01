# CCAT Analysis

**Purpose:** Everything known about the Criteria Cognitive Aptitude Test, translated into a scoring strategy.
**Created:** 31 October 2026
**Last updated:** 31 October 2026
**Research status:** Official Criteria documentation + corroborating independent sources
**Confidence:** High for standard CCAT format; medium for Amber's use of it
**Cross-references:** `../04_CCAT_PREPARATION/*`, `assessment_hypotheses.md`

---

## 1. What the CCAT is

The Criteria Cognitive Aptitude Test (CCAT) is a pre-employment cognitive aptitude assessment published by Criteria Corp. It measures critical thinking, problem solving, learning ability, and the ability to digest and apply new information.

Criteria states it is used for mid- to high-level roles and has high predictive validity for software engineers and other technology workers.

**Important distinction:** The CCAT is not a programming test. It tests general cognitive speed and accuracy. Programming knowledge will not compensate for slow arithmetic or weak vocabulary.

---

## 2. Verified format

| Feature | Detail | Source |
|---|---|---|
| Questions | Up to 50, multiple choice | Criteria official |
| Time | 15 minutes | Criteria official |
| Ability areas | Verbal, Math & Logic, Spatial Reasoning | Criteria official |
| Calculator | Not permitted | Criteria official |
| Completion | Very few finish all 50; <1% per Criteria | Criteria official |
| Scoring | Raw score (correct out of 50) + percentile | Criteria official |
| Wrong-answer penalty | None; explicitly stated in candidate guide | Criteria official; rechecked 31 Oct 2026 |
| Navigation | One question per screen, forward-only | Independent (corroborated) |
| Difficulty | Generally increases; mixed types | Independent (corroborated) |
| Norm mean | 24.2 | Criteria standardization sample |
| Norm median | 24 | Criteria |
| Norm SD | 8.58 | Criteria |

**Do not assume** Amber uses the exact standard form. The invitation says "CCAT," which strongly suggests Criteria's test, but the employer could use a variant or a different provider with a similar name.

---

## 3. Pacing math

- 15 minutes = 900 seconds.
- 50 questions = 18 seconds per question if finishing.
- Realistic target: attempt 40–45, answer 30–35 correctly.
- If you spend 60 seconds on one hard question, you lose ~3 easy questions.

### Time budget that works

| Segment | Time | Questions | Strategy |
|---|---:|---:|---|
| First pass | 9 min | ~30 | Answer quickly; skip anything >30 sec |
| Second pass | 4 min | ~10 | Return to skipped items if navigation allows |
| Final minutes | 2 min | remaining | Shorten hard-item decisions; keep solving immediate items |

If the platform is forward-only, there is no second pass. In that case, guess immediately and move.

---

## 4. Question categories

### 4.1 Verbal ability

Criteria describes verbal questions as measuring reading comprehension, logic, and attention to detail through sentence completion, vocabulary, and word comparison.

Common formats:
- Synonyms and antonyms
- Analogies
- Sentence completion
- Odd word out
- Syllogisms / logical statements
- Attention to detail (string matching)

**What helps:**
- Vocabulary breadth (hard to build in 2 days; focus on common GRE-style words).
- Relationship mapping for analogies (function, category, degree, part-whole, cause-effect).
- Formal logic for syllogisms (all/some/no; valid vs. true).
- Slow, precise reading of short passages.

**What hurts:**
- Choosing a word because it "sounds right."
- Confusing "opposite" with "not similar."
- Overthinking a single vocabulary item.

### 4.2 Math and logic

Criteria groups numerical reasoning and logic under "Math and Logic."

Common formats:
- Arithmetic (fractions, decimals, order of operations)
- Percentages, ratios, proportions
- Averages
- Word problems (rate, work, cost, mixture)
- Number series
- Data interpretation (tables, charts)
- Basic algebra
- Logical deduction / arrangement

**What helps:**
- Mental math shortcuts.
- Translating words into equations.
- Estimating before calculating.
- Checking units and reasonableness.

**What hurts:**
- Full written calculation for every step.
- Getting stuck on one multi-step problem.
- Misreading "percent of" vs. "percent increase."

### 4.3 Spatial reasoning

Common formats:
- Shape series / next in sequence
- 3×3 matrix patterns
- Odd one out
- Rotation and reflection
- Paper folding / hole punching
- Cube nets

**What helps:**
- Tracking one feature at a time (number of sides, orientation, fill, position).
- Verbalising the rule: "rotates 90° clockwise each step."
- Eliminating impossible options.
- Practising with paper for folding problems.

**What hurts:**
- Trying to hold the whole image in memory.
- Assuming a rule from one example.
- Ignoring small details (dot position, shading).

### 4.4 Distribution

Independent sources estimate roughly:
- Verbal: ~30–34%
- Math and logic: ~33–45%
- Spatial: ~20–33%

This is **not official** and varies by form. Do not memorise precise counts. Expect all three early and throughout.

---

## 5. Scoring and target

The provider reports a raw number correct and a percentile against its norm population. Its candidate guide says the average test taker gets about 24 correct. That is not a national population statistic. Consult the actual provider score report for a percentile; do not estimate one from a normal curve or transfer it to these homemade sets.

**Local practice goal:** work toward 30 correct and 40 substantive attempts on the original full drills, then review errors. This is a personal goal, not a calibrated CCAT equivalent, guaranteed attainable improvement or employer threshold. Amber's cut-off and use of the score are UNKNOWN. Track raw score plus substantive accuracy and blind guesses separately.

---

## 6. Strategy

### 6.1 The 3-pass rule (if navigation allows)
1. **Pass 1 — harvest:** answer all easy items in under 20 seconds. Skip the rest.
2. **Pass 2 — solve:** return to skipped items with 30–40 seconds each.
3. **Pass 3 — guess:** fill every blank.

If forward-only: one pass, 20-second decision rule, guess and move.

### 6.2 The 20-second rule
At 20 seconds, decide:
- **Solve now** if the method is obvious.
- **Guess and flag** if it needs more than two steps.
- **Never** spend 60+ seconds on one item.

### 6.3 Triage heuristics
| Question type | Fast to solve? | Action |
|---|---|---|
| Antonym/synonym | Yes, if word known | Answer in 5–10 sec |
| Sentence completion | Usually | Read whole sentence, predict word |
| Analogy | Usually | Map relationship first |
| Attention to detail | Yes, but error-prone | Compare chunk by chunk |
| Arithmetic | Yes | Estimate, then exact |
| Percentage/ratio | Usually | Convert to fractions |
| Number series | Varies | Check differences, ratios, alternating patterns |
| Word problem | Often slow | Skip if >2 steps |
| Table/chart | Medium | Read the question before the data |
| Spatial series | Varies | Track one feature at a time |
| Matrix | Often slow | Check rows then columns |
| Syllogism | Fast if formal | Draw a simple set diagram |

### 6.4 Guessing
There is no penalty. Always guess.
- Eliminate obviously wrong options first.
- Prefer the option that satisfies the most constraints.
- For number series, test the simplest pattern before complex ones.
- For spatial, eliminate options that change a feature that should stay constant.

### 6.5 Scratch paper layout
Divide the page into a 3×3 grid. Use one box per calculation. This prevents carrying errors and makes review faster.

---

## 7. Two-day preparation plan

### Day 1 (31 Oct)
| Time | Activity |
|---|---|
| 30 min | Learn the format and pacing rules |
| 15 min | Take Mock A strictly |
| 45 min | Review every error; classify by cause |
| 30 min | Drill weakest category (20 questions) |
| 20 min | Memorise 10 math shortcuts |
| 15 min | Vocabulary warm-up (20 words) |

### Day 2 (1 Nov)
| Time | Activity |
|---|---|
| 15 min | Take Mock B strictly |
| 30 min | Review and compare with Mock A |
| 30 min | Drill second-weakest category |
| 20 min | Spatial reasoning practice |
| 10 min | Final pacing rehearsal (10 questions in 3 min) |

### Day 3 (2 Nov, morning)
- 10 easy items to warm up.
- No new concepts.
- Review the one-page shortcut sheet.

---

## 8. Error taxonomy

After each mock, label every error:

| Code | Meaning | Fix |
|---|---|---|
| K | Knowledge gap (didn't know word/formula) | Learn the specific item |
| M | Misread question | Slow down on the question stem |
| C | Calculation error | Use scratch paper, estimate first |
| P | Pacing (ran out of time) | Apply 20-second rule |
| L | Logic error | Draw the relationship |
| S | Spatial error | Track one feature at a time |
| G | Guess (no method) | Learn the method for that type |

Track counts. If P dominates, practise skipping. If C dominates, practise arithmetic. If K dominates, vocabulary is the bottleneck (harder to fix in 2 days; accept and optimise elsewhere).

---

## 9. Test-day protocol

1. Read the on-screen instructions fully.
2. Confirm timer and question count.
3. Take one breath; set posture.
4. Start with a quick scan of the first question; do not rush the first 5.
5. At halfway, check the clock. If behind, increase guessing.
6. In the final minutes shorten hard-item decisions and guess when stuck; still solve obvious items. Do not abandon two full minutes of solving merely to click random answers.
7. Do not review answers you cannot change.

---

## 10. What not to do

- Do not try to finish all 50 at the cost of accuracy.
- Do not spend time on a question you cannot solve in 45 seconds.
- Do not leave blanks.
- Do not use a calculator (not allowed).
- Do not panic if the first question is hard; the test is mixed.
- Do not practise only your strongest category.
- Do not memorise leaked questions; they are proprietary and unreliable.

---

## 11. Originality and ethics

All practice questions in this project are original. They follow publicly described formats but are not copied from Criteria, JobTestPrep, or any leaked source. CCAT is a trademark of Criteria Corp.; this project is not affiliated with or endorsed by Criteria.

---

## 12. Source anchors

- Criteria CCAT product page: https://www.criteriacorp.com/assess/cognitive-aptitude/criteria-cognitive-aptitude-test-ccat
- Criteria candidate guide: https://www.criteriacorp.com/candidates/ccat-prep
- Criteria Information Brief: https://www.criteriacorp.com/files/Criteria-InfoBrief-CCAT.pdf
- Criteria Score Report Guide: https://www.criteriacorp.com/files/Criteria-ScoreReportGuide-CCAT.pdf
- Criteria Assessment Guide: https://www.criteriacorp.com/files/Criteria-AssessmentGuide-AssessmentTypes.pdf

Retrieved 31 October 2026.
