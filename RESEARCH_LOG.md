# Research Log

**Purpose:** Chronological record of research activity, findings, source quality, and unresolved questions.
**Created:** 31 October 2026
**Last updated:** 1 November 2026
**Research window:** 31 October 2026, ~1 session
**Note:** Entries record what was actually retrieved. Where a page could not be rendered, that is stated.

---

## Entry 0 — Workspace and document inspection

**Time:** 31 Oct 2026, morning
**Action:** Inspected workspace `bmad-opencode-pilot` and `D:\Lamaran`.
**Found:**
- Workspace contains BMAD skills and review folders; no existing Amber research.
- `CV_Marchel_Karuna_Kwee.pdf` (updated 16 Oct 2026), `Portfolio_Marchel_Karuna_Kwee.pdf` (19 Oct 2026), transcript, SKPI, diploma.
- No recruitment invitation, email export, or assessment attachment was present.
- CV and portfolio text extracted with `pypdf`.

**Key candidate facts extracted:**
- B.Sc. Informatics Engineering, ITERA, Aug 2022–Jul 2026, GPA 3.60/4.00.
- Backend Developer Intern, Kementerian PPN/Bappenas, Jun–Jul 2025; PHP, CodeIgniter, MySQL; four-person Agile team; Jira, GitLab.
- Full-stack developer for SMB Suvanna Dipa (Next.js, TypeScript, PostgreSQL, Supabase; RFID attendance integrated with an IoT engineer).
- Other projects: Iterary (React, MySQL, Docker, Redis, Google Cloud; cloud engineer), Kibang Soil Tracker (Next.js, Firebase; project manager), Simonika (PHP, CodeIgniter, MySQL; backend), Lebung Farm (JavaScript, Bootstrap, Figma; UI/UX + frontend), Nitro Itera Racing (Python/Pygame; game programmer), Legenda Tiga Raja (Godot/Aseprite; game artist).
- CV self-rates English as "Limited Working Proficiency."

**Confidence:** VERIFIED (primary candidate documents).

**Gap:** The actual invitation email and any attachment were not supplied. The prompt's summary is treated as the authoritative recruitment brief, but not as a primary document.

---

## Entry 1 — Company identity

**Sources retrieved:**
1. Official website, Who We Are: https://www.ambersof.com/en/who-we-are/who-we-are
2. Official website, Solutions: https://www.ambersof.com/en/solutions
3. Official website, Custom Development: https://www.ambersof.com/en/solutions/custom-development
4. Official website, Updates index: https://www.ambersof.com/en/updates
5. Official website, Customer Testimony: https://www.ambersof.com/en/who-we-are/customer-testimony
6. LinkedIn company page: https://www.linkedin.com/company/ambersof
7. Glints company profile: https://glints.com/id/en/companies/pt-amber-solusi-internasional/7bc340b4-b1bc-4942-a9d0-8ad93f00537d
8. Jobstreet employer page: https://id.jobstreet.com/companies/amber-solutions-international-168552074959653
9. Kalibrr employer page: https://www.kalibrr.id/c/pt-amber-solusi-internasional/jobs
10. Dealls company page: https://dealls.com/karir/pt-amber-solusi-internasional
11. Epicareer company page: https://id.epicareer.com/companies/pt-amber-solusi-internasional
12. RevenueBase company profile: https://revenuebase.ai/companies/profiles/ambersof

**Findings:**
- Legal name: PT Amber Solusi Internasional; brand "Ambersof"; tagline "Talent & Technology" / "Innovation is in our DNA."
- Founded 2016; privately held; IT services and consulting.
- HQ address per LinkedIn: Gading Bukit Indah, Jl. Raya Gading Kirana No.17 Blok A No.17, Kelapa Gading Barat, North Jakarta 14420.
- Glints job posting gives office address: Scientia Business Park Tower 2, Lantai 2, Jl. Boulevard Gading Serpong Blok O/2, Curug Sangereng, Kelapa Dua, Serpong, Banten 15810.
- Kalibrr and Dealls also list Tangerang. Multiple office locations are plausible; exact assessment-related location is irrelevant because the assessment is online.
- Headcount: LinkedIn ~49 employees; most job portals say 11–50 or 50–100. Treat as approximately 50, not a precise figure.
- Delivery markets: Indonesia, Singapore, New Zealand, United States (official). Some older profiles say Singapore and Malaysia (inconsistent; likely outdated).
- Positioning: enterprise transformation through AI, intelligent automation, data, and enterprise technology; "we don't just build technology, we build intelligent solutions."
- Named clients/testimonials: Telkomsel, Natural Way of Living (Lotus Garden), Pacific Star Corporation, Cinema XXI, IPC (showcase).
- Revenue figures: none public. Do not estimate as fact.

**Classification:** VERIFIED for official-site and LinkedIn claims; CORROBORATED for founding year and industry; REPORTED for headcount and client relationships from third-party portals.

**Contradictions:**
- Employee count varies (11–50, 40+, 49, 50–100, 51–200). `REPORTED`.
- Older descriptions emphasise Oracle; the current site emphasises AI/automation plus Oracle, Odoo, Dynamics 365. This is consistent with repositioning, not necessarily contradiction.

---

## Entry 2 — Products, services, and technology signals

**Sources:**
- Official Solutions page (retrieved 31 Oct 2026).
- Official Custom Development page.
- Official Updates index (246 records, latest 27 Oct 2026).
- FOOMA references on Instagram and official posts.
- Archived Fresh Graduate Programmer posting on Glints.
- Public LinkedIn profiles of Amber technical staff (search snippets only).

**Services identified:**
- Oracle implementation services
- Odoo ERP implementation
- Microsoft Dynamics 365 implementation
- Intelligent stockpile monitoring (fixed-camera photogrammetry, AI, computer vision)
- Custom development (web, mobile, enterprise, API, cloud, automation, modernization, database, dashboards)
- IT blueprint
- Talent services
- SEVICO field inspection and operation
- FOOMA (own product): financial data automation/integration; unify disconnected data, automate validation, accelerate month-end close, integrate to ERP.

**Technology signals:**
- Public job ads across the company mention PHP, .NET/C#, Java, Angular, Flutter, Next.js, FastAPI, Python, AWS, SAP, Oracle, Microsoft 365/Power Platform, Azure.
- The specific Fresh Graduate Programmer ad lists: .NET, Flutter, Java, Angular.js, PHP.
- Employee profile (Idham Mansyah Awwalu, Fullstack Developer – Middle, Apr 2026–present) lists PHP/Laravel/CodeIgniter, Java Spring Boot, Vue.js/TypeScript, Flutter, MySQL, REST API, JWT.
- Another profile lists Oracle/PeopleSoft/AWS consulting exposure (search snippet; lower confidence).
- Do **not** infer that the fresh graduate will choose a stack. The ad says "interested in learning and developing applications using Java, PHP, Angular, .NET, and Flutter." This is a generalist programmer role.

**Classification:** VERIFIED for services and ad skills; REPORTED for employee technology use; INFERRED for "generalist consulting delivery" positioning.

---

## Entry 3 — The actual job posting

**Source:** Glints, "Fresh Graduate Programmer," PT Amber Solusi Internasional.
**URL:** https://glints.com/id/en/opportunities/jobs/fresh-graduate-programmer/57dc25b6-6867-4088-bc74-01e7b157a967
**Retrieved:** 31 October 2026.
**Status on retrieval:** "This job was closed."
**Compensation shown:** Rp 6,000,000–7,000,000/month.
**Type:** Contract, on-site, minimum bachelor's degree, less than one year experience.
**Skills tags:** .NET, Flutter, Java, Angular.js, PHP.
**Job description (verbatim key points):**
1. Recent graduate in IT-related field.
2. Passionate about programming and eager to build a career as a professional programmer.
3. Solid understanding of basic programming concepts, "not just SELECT * FROM table_name."
4. Interested in learning and developing applications using Java, PHP, Angular, .NET, and Flutter.
5. Resourceful and willing to research solutions; "Oppa Google is always there to help."
6. Common sense: know when to research independently and when to ask for advice or brainstorm with seniors.
7. Growth mindset and openness to feedback.
8. "Believe in working with harmony between brain and heart."
**Managed by:** "Savitri Savitri" (profile display name; likely HR/recruiter).
**Office address:** Scientia Business Park Tower 2, Gading Serpong, Tangerang.

**Why this matters:**
- Confirms generalist expectations across five technology families.
- Confirms SQL/database fundamentals are explicitly tested in conversation ("not just SELECT *").
- Confirms learning attitude and asking-for-help are explicit selection criteria.
- The closed status means this is likely the same role family but not necessarily the exact requisition; the assessment may differ.

**Classification:** VERIFIED (public ad content); INFERRED (same requisition as the Nov 2 assessment).

---

## Entry 4 — Recruitment process intelligence

**Sources:** Jobstreet listing for Fresh Graduate System Analyst (closed); Glints Fresh Graduate Business Analyst (closed); Glints Programmer (.NET) (closed); public LinkedIn posts; no candidate reports found.

**Findings:**
- Amber hires fresh graduates into multiple tracks: Programmer, System Analyst, Business Analyst.
- Public ads consistently mention English, problem solving, documentation, teamwork, and "decent English."
- No public description of the CCAT administration or "Programmer Business Case" was found.
- No Glassdoor page specific to PT Amber Solusi Internasional was located; search results returned unrelated "Amber" companies. Do not use those reviews.
- No verified candidate account of Amber's assessment was found.

**Classification:** REPORTED for hiring patterns; UNKNOWN for assessment content and rubric.

**Critical caution:** Any claim about Amber's exact CCAT cut-off, business-case prompt, or number of interview rounds would be fabricated.

---

## Entry 5 — CCAT provider research

**Sources:**
1. Criteria official CCAT page: https://www.criteriacorp.com/assess/cognitive-aptitude/criteria-cognitive-aptitude-test-ccat
2. Criteria candidate guide: https://www.criteriacorp.com/candidates/ccat-prep
3. Criteria CCAT Information Brief PDF: https://www.criteriacorp.com/files/Criteria-InfoBrief-CCAT.pdf
4. Criteria Score Report Guide PDF: https://www.criteriacorp.com/files/Criteria-ScoreReportGuide-CCAT.pdf
5. Criteria Assessment Guide PDF: https://www.criteriacorp.com/files/Criteria-AssessmentGuide-AssessmentTypes.pdf
6. Independent format analyses (JobTestPrep, CCAT Practice Test, PrepCCAT, TestCCAT, CCAT Ready) — secondary, used only for question-type breakdown and pacing.

**Verified facts:**
- Up to 50 multiple-choice questions; 15 minutes.
- Three ability areas: verbal ability, math and logic, spatial reasoning.
- No calculators.
- Very few candidates finish all 50 (<1% per Criteria).
- Raw score = number correct; percentile vs. norm group.
- Norm mean 24.2, median 24, SD 8.58 (Criteria standardization sample).
- No wrong-answer penalty stated by Criteria; independent sources agree.
- Question types are interleaved, not sectioned.
- One question per screen and forward-only per independent sources (not explicitly confirmed on Criteria page).

**Disputed / uncertain:**
- Exact category percentages vary by source: roughly verbal 30–34%, math/logic 33–45%, spatial 20–33%. Use approximate ranges, not precise counts.
- "Logical reasoning" is not a separate official section; it sits inside math and logic and some verbal items.
- Whether Amber's invitation uses standard CCAT or a variant is unknown.

**Classification:** VERIFIED for official format and scoring; CORROBORATED for interleaving and no penalty; HYPOTHESIS for Amber's use of the standard form.

---

## Entry 6 — Social media and content scan

**Sources (public snippets only):**
- Instagram @ambersof_: https://www.instagram.com/ambersof_/
- Facebook page: https://www.facebook.com/PT-Amber-Solusi-Internasional-100264922319921/
- X/Twitter: https://twitter.com/Ambersof_
- LinkedIn company updates: https://www.linkedin.com/company/ambersof
- Official Updates blog: https://www.ambersof.com/en/updates

**Observed themes and dated examples:**
- 29 Jun 2026: FOOMA explainer reel — unify financial data, automate validation, accelerate month-end close.
- 25–26 Jun 2026: FOOMA posts — eliminate manual data entry, connect disconnected systems, integrate to ERP.
- 15 Jul 2026: "We're Hiring Technical Lead (.NET)" — remote/hybrid/WFO.
- 21–22 Jul 2026: employer-branding/article posts, including "#TalentNetwork" content.
- 9 Aug 2026: "We're Hiring SAP FICO Consultant" — remote/hybrid/WFO.
- 15 Oct 2026: LinkedIn post on AI and human thinking; AWS Cloud Engineer hiring post.
- 27 Oct 2026: blog "Odoo for Property Management."
- 14 Oct 2026: blog "Why Odoo for Your Mining Business?"
- 9 Oct 2026: blog "Ambersof: Your Odoo ERP Technology and Implementation Partner."
- 10 Jul 2026: blog "Why Software Testing Is More Than Just Finding Bugs."
- 15 Jul 2026: blog "Is Gen Z Turning Instagram Into the New LinkedIn?"

**Limitations:**
- Instagram and LinkedIn were not fully browsable chronologically; only public snippets surfaced via search.
- No OCR was performed on post images beyond alt-text/description available in search results.
- Follower counts fluctuate; not material.

**Classification:** REPORTED (public posts). Do not treat individual posts as company policy.

---

## Entry 7 — Culture and employee signals

**Sources:** Official "Who We Are," "Our DNA" (navigation label; page content not directly retrievable), Dealls culture section, job ads, LinkedIn employee snippets.

**Findings:**
- Stated values: passionate, fast-paced, innovative; "people and engineering"; "harmony between brain and heart"; "we don't need superstars, we need super team."
- Learning and competence development are explicitly valued.
- International delivery exposure (Indonesia, Singapore, New Zealand, US) implies English communication.
- Employee profiles show a mix of junior and senior staff, with mid-level full-stack developers working across legacy PHP and modern Vue/Java/Flutter.
- No reliable employee-review data specific to this company was found. Do not infer toxicity or excellence.

**Classification:** VERIFIED for stated values; REPORTED for employee profiles; UNKNOWN for actual day-to-day culture.

---

## Entry 8 — Candidate positioning analysis

**Action:** Mapped CV/portfolio evidence to the job ad.

**Strong matches:**
- Full-stack web delivery with Next.js/TypeScript/PostgreSQL/Supabase.
- Backend internship with PHP/CodeIgniter/MySQL in a four-person team.
- SQL use across academic and internship projects.
- Requirements-to-implementation experience (SMB Suvanna Dipa, Simonika).
- Documentation and project management exposure (Kibang Soil Tracker, Bappenas).
- Team collaboration, stakeholder coordination, Git/Jira/GitLab/Docker.

**Partial matches:**
- Java: no project or coursework evidence supplied. Do not infer academic exposure from the degree.
- Angular: no evidence. Transferable from React/Next.js component thinking.
- .NET: no evidence. Transferable OOP from C++/Python/TypeScript.
- Flutter: no evidence. Transferable mobile-adjacent UI and API integration; no shipped Flutter app.

**Gaps:**
- CCAT speed under pressure (no prior score).
- Live business-case presentation in English.
- SQL depth beyond CRUD (joins, aggregation, subqueries, indexing).
- Explaining trade-offs and non-functional requirements.
- English speaking fluency (self-rated limited).

**Classification:** INFERRED from documents; must be validated by mock performance.

---

## Open research questions

| ID | Question | Why it matters | How to resolve |
|---|---|---|---|
| RQ-01 | Which platform hosts the CCAT? | Confirms format and navigation | See invitation / on-screen intro |
| RQ-02 | Is the business case written, spoken, or coding? | Changes preparation emphasis | Ask recruiter or read instructions |
| RQ-03 | Are there additional interviews on 2 Nov? | Time/energy allocation | Invitation or recruiter |
| RQ-04 | Is the role based in Gading Serpong or North Jakarta? | Logistics only if onsite later | Recruiter |
| RQ-05 | What is the expected tech stack for this cohort? | Depth vs. breadth | Ask during case/interview |
| RQ-06 | Is there a minimum CCAT percentile? | Target setting | Not public; assume competitive |
| RQ-07 | Will the candidate be allowed to choose a language for coding? | Fairness | Ask before task |
| RQ-08 | Is the contract length/renewal path clear? | Motivation answer | Ask HR |

---

## Source reliability summary

| Source type | Examples | Reliability | Use |
|---|---|---|---|
| Official website | ambersof.com | High for stated services/values; marketing bias | Company facts |
| Official LinkedIn | linkedin.com/company/ambersof | High for identity; self-reported | Identity, headcount approx. |
| Job advertisements | Glints, Jobstreet | High for requirements; may be stale | Role expectations |
| Assessment provider | criteriacorp.com | Highest for CCAT format | CCAT strategy |
| Third-party company data | RevenueBase, Tracxn, Epicareer | Medium; often scraped/outdated | Corroboration only |
| Social media snippets | Instagram/LinkedIn posts | Medium; context may be missing | Timeline/themes |
| Employee profiles | LinkedIn | Medium; self-reported | Tech signals only |
| Glassdoor | none specific found | Not applicable | Do not use unrelated companies |

---

## Research limitations

1. No access to the actual recruitment email or invitation attachment.
2. No access to Amber's internal assessment materials, rubric, or candidate history.
3. Instagram/LinkedIn content not exhaustively crawlable; timeline is partial.
4. Some official pages are JavaScript-rendered and returned empty text via direct fetch; content was recovered through search-engine renderings. This is noted rather than hidden.
5. Headcount and office data conflict across portals; ranges are given.
6. No verified candidate experience reports exist in public search results.

---

## Next research actions (only if time permits)

1. Ask the recruiter two precise questions: assessment format and whether coding is required.
2. Re-check the Glints/Jobstreet posting for an updated requisition.
3. If the invitation names a CCAT platform, verify its navigation and rules.
4. Do not spend more time on company history; marginal value is low compared with CCAT practice.

---

## Entry 9 — Continuation audit and writing scope

**Date:** 31 October 2026. Rechecked existing files before continuing.

- Root tracking files claimed completion for sections not yet written. Corrected active status; final audit will replace the premature inventory.
- CCAT guides, three original mock sets, keys, drills, and 60 bilingual interview items exist. These mocks are educational, not psychometrically equivalent to CCAT; mock-to-percentile or employer-pass predictions are not justified.
- Candidate fact sheet contained unsupported extrapolations (schema ownership, quantified competence, work preferences, deployment scope). Primary CV/portfolio must override that sheet. Unknown links between Simonika and the internship must remain unknown, not be declared either identical or separate projects.
- Specific bugs, conflicts, test coverage, implementation decisions and relocation availability are not documented. They must be prompts or hypothetical practice, never scripted biography.
- This entry records local authoring/audit, not new web retrieval. Existing retrieval dates refer to earlier log entries.

**Next:** complete missing sections, correct known content defects, validate question counts/metadata and local references. No live performance assessment has occurred.

---

## Entry 10 — Preparation sections authored and provider rules rechecked

**Date:** 31 October 2026.

- Wrote technical guides (including 20 PostgreSQL query exercises, 15 algorithm drills and 100 glossary terms), four explicitly fictional worked business cases, English rehearsal materials, modes A–F with blank reports, candidate evidence/gap materials, learning resources and final checklists.
- Completed question-bank categories SQL, software engineering, behavioural/situational and business case. Counts now total 120 in the requested 15/15/10/20/15/15/15/15 distribution.
- Replaced unsupported personal stories in earlier items with documented scope, proposed reasoning or explicit real-incident prompts. No fake conflict, bug, missing test suite or relocation commitment is supplied as biography.
- Corrected ambiguous cube nets, existential logic premises, a verbal analogy key, and misleading local-mock score interpretations. Marked the full sets' template overlap and graphical-practice limitations.
- Directly re-fetched https://www.criteriacorp.com/candidates/ccat-prep on 31 October 2026. It explicitly confirms 50/15, no calculator, three domains, fewer than 1% answer all items and no wrong-answer penalty. It does not establish Amber's cut-off, exact navigation or allowed scratch paper. See `sources/assessment_provider_notes.md`.
- New technical/English resource recommendations were compiled, not newly fetched; do not assign them a fabricated retrieval date.

**Verification boundary:** SQL has not been executed against PostgreSQL; speaking/coding/business-case/cognitive performance remains unmeasured. Final structural audit is recorded separately in `sources/verification_report.md`.

---

## Entry 11 — User-reported empty areas and correction of completion claim

**Date:** 31 October 2026.

The user challenged the claim that all documents were complete. A recursive filesystem check confirmed 13 empty scaffold subfolders and no zero-byte files. Several case/mock documents had been written at alternative paths instead of the prescribed nested locations. Five source-collection directories also remain empty; root-level research notes do not mean those artifacts were collected.

The earlier verification covered file existence, question counts/metadata and local links, not full path/content compliance. Its overall completeness implication is withdrawn. README, tracker and verification report now explicitly mark the package incomplete. Personal incident templates and blank practice-result reports are separately identified; neither should be presented as completed candidate answers or observed performance.

No source artifact, personal incident or practice result was invented to conceal these gaps. The directory structure had not yet been reconciled at that corrective status update; the subsequent repair is recorded below.

---

## Entry 12 — Requested remaining authoring and structure work repaired

**Date:** 1 November 2026.

**Work performed:**

- Moved four full cases into case_studies, schema/API examples into database_design and the rubric into solution_evaluations. Retained small compatibility links at the old locations rather than break existing references.
- Added solved relational exercises, architecture/write-path/failure walkthroughs for all four cases, and a fully labelled fictional weak-answer evaluation with an improved response.
- Reconciled English, technical and programmer-business-case mock paths. Added ready-to-run timed scripts, a candidate-only case brief, canonical result navigation and an explicitly fictional scoring demonstration. No actual candidate scores were filled.
- Added a speakable honest-fallback guide and Indonesian remaining-day route `MULAI_BELAJAR.md`, because the user needs to study rather than inspect file inventories.

**Direct source collection:**

- Official homepage https://www.ambersof.com/en returned no useful Markdown body; browser rendering exposed service text, update titles and linked official accounts. Retained a separately downloaded 136,514-byte HTML response.
- Criteria guide https://www.criteriacorp.com/candidates/ccat-prep was re-fetched; retained its 55,135-byte HTML response and selected rules, without copying proprietary questions.
- The exact Glints programmer ad was fetched as Markdown and still says closed, Rp6–7M/month, contract/on-site and the advertised five-stack/fundamentals requirements. A separate raw HTTP attempt returned 403; recorded that failure instead of inventing a local HTML archive.
- Public https://www.linkedin.com/company/ambersof/ and https://www.instagram.com/ambersof_/ returned bounded material. Retained observations, specific post URLs and limits. LinkedIn profile-size band, employee-profile count and the job-portal band disagree; none is a precise headcount.
- Downloaded the exact official-logo PNG exposed by the company page, checked its signature and SHA-256 and recorded provenance. No invitation screenshot or protected test image was manufactured.
- Filled recruitment_documents with a provenance-labelled supplied-brief record and missing-original status ledger. The invitation itself remains unavailable.

**Final checks:** 148 files (143 Markdown, 2 extracted text, 2 raw HTML, 1 PNG); all 13 reported subfolders have specified material/evidence/status records; zero empty folders/files; no broken checked local references or unbalanced Markdown fences; bank remains 120 unique sequential IDs and 14 fields per item. Source hashes match retained bytes. SQL execution and candidate-performance testing were not performed. See `sources/verification_report.md` for scope, not a blanket completeness or readiness guarantee.
