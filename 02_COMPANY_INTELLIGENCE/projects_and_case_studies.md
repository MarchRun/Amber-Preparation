# Projects and Case Studies

**Purpose:** Document publicly observable Amber projects without inventing confidential details.
**Created:** 31 October 2026
**Last updated:** 31 October 2026
**Research status:** Public marketing pages and posts only
**Confidence:** Medium for existence; low for technical detail

---

## 1. Publicly referenced projects

### 1.1 Telkomsel — finance transformation

**Evidence:** Customer testimonial on the official site.
**Stated scope:** "Helping us with our finance transformation project."
**What is public:** The relationship and the general domain (finance transformation).
**What is not public:** Systems replaced, modules, timeline, team size, architecture, results.
**Interview use:** "I saw that Telkomsel mentions a finance transformation project with your team. That kind of work seems to require both technical integration and process understanding."
**Do not:** Invent metrics, claim to know the solution, or imply the project is still active.

---

### 1.2 IPC — Oracle E-Business Suite and Procurement

**Evidence:** Official showcase listing.
**Stated scope:** "Providing Solutions with Oracle E-Business Suite and Procurement Module for PT. IPC."
**Domain:** Port/logistics enterprise; procurement.
**Likely technical themes:** Oracle EBS configuration, procurement workflow, integration, reporting, user roles.
**Interview use:** "The IPC showcase suggests you work on procurement processes inside Oracle EBS, which is a good example of technology plus process design."
**Do not:** Claim knowledge of IPC's internal systems.

---

### 1.3 Natural Way of Living — Lotus Garden

**Evidence:** Official showcase and testimonial.
**Stated scope:** A web-based application built for Natural Way of Living.
**Domain:** Lifestyle/wellness or property brand (name suggests natural living).
**Public detail:** Limited to the showcase description.
**Interview use:** "Lotus Garden looks like a customer-facing web application. I have built public landing pages and internal dashboards, so I understand the split between presentation and operational data."
**Do not:** Assume e-commerce, booking, or CMS without evidence.

---

### 1.4 Pacific Star Corporation — resourcing/testimonial

**Evidence:** Customer testimonial about "providing us the best resources."
**Interpretation:** Likely talent services or staff augmentation rather than a software build.
**Interview use:** Mention only if discussing the talent-services line. Do not present it as a development project.

---

### 1.5 Cinema XXI — delivery responsiveness

**Evidence:** Customer testimonial praising efficiency, directness, and fast response.
**Interpretation:** Likely a software or consulting engagement; details not public.
**Interview use:** Supports the claim that responsiveness is part of the company's service identity.

---

## 2. Service case studies (composite, clearly hypothetical)

These are **not** Amber projects. They are realistic scenarios used for practice, modelled on the service lines.

### Case A — Procurement approval workflow

**Client type:** Mid-size manufacturer using Oracle EBS.
**Problem:** Purchase requests are approved over email; no audit trail; duplicate orders.
**Solution shape:** Workflow engine, role-based approvals, budget checks, ERP integration, audit log, dashboard.
**Key trade-offs:** Configuring Oracle workflow vs. building an external approval app; latency vs. auditability; mobile approval vs. security.
**Why relevant:** Matches Amber's Oracle/procurement showcase and enterprise client base.

### Case B — Multi-outlet inventory sync

**Client type:** Retail chain.
**Problem:** Stock counts differ between POS, warehouse, and finance; month-end reconciliation takes days.
**Solution shape:** Integration layer, event-driven stock movements, idempotent updates, reconciliation report, exception queue.
**Key trade-offs:** Real-time vs. batch; consistency vs. availability; custom sync vs. ERP module.
**Why relevant:** Matches FOOMA's financial data integration theme.

### Case C — Field inspection mobile app

**Client type:** Infrastructure operator.
**Problem:** Inspectors use paper forms; data arrives late; photos are unmanaged.
**Solution shape:** Flutter/offline-first mobile app, photo capture, sync queue, conflict resolution, web dashboard, role-based access.
**Key trade-offs:** Offline capability vs. development cost; photo storage cost vs. audit needs; device diversity.
**Why relevant:** Matches SEVICO and the Flutter requirement.

### Case D — Stockpile volume monitoring

**Client type:** Mining operation.
**Problem:** Manual volume surveys are slow and inaccurate.
**Solution shape:** Fixed cameras, image capture, photogrammetry, volume estimation, dashboard, ERP inventory integration, human review.
**Key trade-offs:** Accuracy vs. cost; camera placement vs. coverage; automation vs. safety review.
**Why relevant:** Matches Amber's intelligent stockpile monitoring service.

---

## 3. What these cases teach about Amber's work

| Pattern | Implication for a junior programmer |
|---|---|
| Enterprise clients with existing systems | Integration and data mapping matter more than greenfield coding |
| Finance/procurement domains | Accuracy, auditability, and permissions are critical |
| Multiple platforms | Learn the platform's constraints, not just the language |
| Client-facing delivery | Communication and documentation are part of the job |
| Small teams | Generalists who can test, document, and support are valuable |
| Product + services | Reuse and configuration beat one-off custom code |

---

## 4. Project discussion framework (for Marchel's own projects)

Use this to answer "Tell me about a project" in 2 minutes:

1. **Context:** Client/user and problem.
2. **Role:** What you owned; who else was involved.
3. **Constraints:** Time, team, technology, data.
4. **Action:** Key decisions and trade-offs.
5. **Result:** What worked, what was measured.
6. **Learning:** What you would do differently.

### Example skeleton — SMB Suvanna Dipa
- Context: Sunday school administration for students, mentors, and admins.
- Role: Full-stack developer; RFID integration handled with a separate IoT engineer.
- Constraints: Academic timeline, small team, role complexity.
- Action: Built Next.js/TypeScript app on PostgreSQL/Supabase; modelled users/roles; built attendance records; integrated RFID data.
- Result: Operational system for multiple user types; public landing page plus internal features.
- Learning: Clear role boundaries and data validation matter; would add automated tests earlier.

**Do not claim:** You built the RFID hardware or firmware.

---

## 5. Questions to ask about projects (if given the chance)

1. "Which of these service lines would a fresh graduate most likely support?"
2. "Are projects usually greenfield or maintenance/integration?"
3. "How does the team handle handover and documentation between consultants and developers?"

---

## 6. Source anchors

- Testimonials: https://www.ambersof.com/en/who-we-are/customer-testimony
- Showcases: https://www.ambersof.com/en/showcases
- Solutions: https://www.ambersof.com/en/solutions
- Homepage highlights: https://www.ambersof.com/en

Retrieved 31 October 2026. Marketing content may omit or simplify details.
