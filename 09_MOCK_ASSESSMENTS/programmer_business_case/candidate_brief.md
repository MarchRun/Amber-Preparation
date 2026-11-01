# Candidate-Only Brief — School Operations

**Created:** 1 November 2026
**Status:** Fictional practice scenario. Not an Amber client, project, or brief.
**Limit:** 45 minutes including a five-minute presentation. No model answer on this page.

## Scenario

A private school operates three campuses. Staff record attendance manually and prepare report cards in spreadsheets. Parents receive inconsistent information. The school wants a practical first release that improves attendance reliability and term reporting. The budget, number of users, connectivity, existing roster system and grading policy have not been supplied.

## Your task

Prepare a one-page proposal and a simple architecture diagram. Address:

1. Up to five questions that would change your solution.
2. Known facts versus explicit assumptions.
3. MVP and exclusions, with a business reason.
4. Main users, workflows and data relationships.
5. Two API contracts, including permission and failure behaviour.
6. One integrity invariant and one concurrency/retry risk.
7. Build/configure or capture-method trade-off with a decision.
8. Privacy, testing, rollout and next validation.

Use technology you can explain; do not claim experience you lack. A proposed target is not an observed metric. If a facilitator cannot answer a question, state an assumption and identify what changes if it is wrong.

## Timing

5 read/clarify; 3 scope; 15 design; 7 risks/tests/trade-offs; 10 prepare; 5 present. For a solo attempt, say your clarification questions aloud and write the assumptions you choose.

## Facilitator follow-up after presentation

Reveal one of these conditions, not all at once:

- Some campuses lose connectivity during attendance capture.
- A guardian must not see a former linked child's records after access is revoked.
- An attendance event arrives after the term report has been released.

Give three minutes to revise. Observe which component, data rule and test change. The intended skill is adapting reasoning, not predicting a hidden preferred stack.

**Catatan ID:** Bagian yang tidak disebutkan jangan dianggap fakta. Mulai dari tujuan, pengguna, batasan dan lingkup; jangan langsung daftar teknologi. Ini latihan asli, bukan bocoran soal perusahaan.
