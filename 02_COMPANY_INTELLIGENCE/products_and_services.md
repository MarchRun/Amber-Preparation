# Products and Services

**Purpose:** Understand each Amber offering well enough to discuss it intelligently and to generate realistic business cases.
**Created:** 31 October 2026
**Last updated:** 31 October 2026
**Research status:** Official service pages reviewed; product internals not public
**Confidence:** Medium-high for service scope; low for technical architecture

---

## 1. Service catalogue

### 1.1 Oracle implementation services

**What it is:** End-to-end implementation and support for Oracle enterprise applications, likely including Oracle E-Business Suite, Oracle Cloud, NetSuite, and related procurement/finance modules.

**Target users:** Enterprises already using or migrating to Oracle; finance, procurement, and operations teams.

**Problems solved:** Fragmented finance data, manual procurement, compliance gaps, legacy Oracle customisations, reporting delays.

**Typical activities:** Requirements workshops, process mapping, configuration, data migration, integration, testing, training, post-go-live support.

**Interview angle:** Oracle implementations are as much about process and change management as code. A programmer's job is often integration, extensions, reports, and data fixes.

**Do not claim:** Knowledge of specific Oracle modules or certifications.

---

### 1.2 Odoo ERP implementation

**What it is:** Implementation, customisation, integration, and optimisation of Odoo modules for finance, sales, inventory, manufacturing, CRM, and HR.

**Target users:** SMEs and mid-market companies seeking an integrated ERP at lower cost than tier-1 platforms.

**Problems solved:** Disconnected sales/inventory/finance processes, manual stock control, poor reporting, duplicated data entry.

**Technical shape:** Python-based Odoo framework, PostgreSQL, XML views, ORM, module customisation, API integrations.

**Why it matters now:** Amber published a series of Odoo articles in October 2026 (property management, mining, partner positioning), suggesting active go-to-market focus.

**Interview angle:** Odoo is a strong example of configuration vs. customisation trade-offs. Custom code increases upgrade risk.

---

### 1.3 Microsoft Dynamics 365 implementation

**What it is:** Implementation, customisation, migration, and integration services for Dynamics 365.

**Target users:** Enterprises standardising on Microsoft's business applications ecosystem.

**Problems solved:** CRM/ERP integration, sales pipeline visibility, finance operations, migration from legacy Microsoft or third-party systems.

**Technical shape:** Likely Power Platform, Dataverse, Azure integration, C#/.NET plugins, Power Automate.

**Interview angle:** The Fresh Graduate Programmer ad lists .NET, so Dynamics exposure is plausible but not guaranteed.

**Do not claim:** Dynamics certifications or project experience.

---

### 1.4 Intelligent stockpile monitoring

**What it is:** Monitoring of stockpiles (likely mining/commodities) using fixed-camera photogrammetry, AI, and computer vision.

**Target users:** Mining, cement, bulk materials, ports, and logistics operations.

**Problems solved:** Manual volume measurement, inaccurate inventory, safety risks, slow reconciliation.

**Technical shape (inferred):** Camera capture, image processing, photogrammetry, volume estimation, dashboard, integration with ERP/inventory.

**Interview angle:** A good example of AI applied to a concrete operational problem, not a generic chatbot.

**Caution:** Technical details are not public; describe at a high level only.

---

### 1.5 Custom development

**What it is:** Tailored web, mobile, enterprise, API, cloud, automation, modernisation, database, and dashboard solutions.

**Scope listed by the company:**
- Enterprise application development
- Web application development
- Mobile application development
- API development and integration
- Cloud-based applications
- Business process automation
- System modernisation
- Legacy system enhancement
- Database design and optimisation
- Custom dashboards and reporting

**Target users:** Clients whose needs cannot be met by off-the-shelf software.

**Problems solved:** Process gaps, legacy systems, integration gaps, reporting needs, customer-facing digital channels.

**Interview angle:** This is the service line most directly aligned with Marchel's experience. Emphasise requirements-to-delivery, not just frameworks.

---

### 1.6 FOOMA

**What it is:** Amber's own financial data automation/integration product.

**Stated capabilities (public posts):**
- Unify disconnected financial data into one workflow.
- Automate validation and processing.
- Speed up month-end closing.
- Transform raw data into structured financial journals.
- Integrate with ERP systems.
- Scale with business growth.
- Handle data mapping and reporting adjustments.

**Target users:** CFOs, finance teams, operations leaders, enterprises with multiple systems.

**Problems solved:** Manual data entry, reconciliation errors, slow closes, disconnected source systems, reporting delays.

**Technical shape (inferred):** Data ingestion, transformation, validation rules, mapping engine, workflow automation, ERP connectors, audit logs.

**Interview angle:** FOOMA is a product-thinking story: reusable connectors and configuration vs. one-off custom scripts. It also raises data integrity, auditability, and security questions.

**Do not claim:** Hands-on FOOMA experience or internal architecture knowledge.

---

### 1.7 IT blueprint

**What it is:** Advisory service to assess an organisation's technology landscape and propose a roadmap aligned with business objectives.

**Target users:** Leadership teams planning transformation.

**Problems solved:** Unclear priorities, fragmented systems, misaligned IT investment.

**Interview angle:** Shows the company sells thinking, not just execution. Business-case answers should therefore show structured thinking.

---

### 1.8 Talent services

**What it is:** Placement, outsourcing, and staff augmentation.

**Target users:** Companies needing specialist skills without permanent hiring.

**Problems solved:** Talent shortages, project peaks, access to niche ERP/cloud skills.

**Interview angle:** This explains why Amber hires contract fresh graduates and values adaptability and quick ramp-up.

---

### 1.9 SEVICO — field inspection and operations

**What it is:** A solution for field inspection and operations (details limited).

**Target users:** Field service, utilities, infrastructure, and operations teams.

**Problems solved:** Paper-based inspections, poor visibility, slow reporting, accountability gaps.

**Interview angle:** Adjacent to FOOMA and stockpile monitoring: digitising operational workflows.

**Caution:** Public detail is thin; do not invent features.

---

## 2. Product/service comparison

| Offering | Buyer | Delivery model | Technical intensity | Junior involvement |
|---|---|---|---|---|
| Oracle implementation | CIO/CFO | Project + support | High, platform-specific | Integration, reports, fixes |
| Odoo implementation | Operations/IT manager | Project + support | Medium-high, Python/PostgreSQL | Module config, customisation |
| Dynamics 365 | CIO/CRM lead | Project + support | High, Microsoft stack | Plugins, Power Platform, integration |
| Custom development | Business owner/IT | Project | High, varied stack | Full-stack features |
| Stockpile monitoring | Operations/plant manager | Project + support | High, CV/AI | Data pipelines, dashboards |
| FOOMA | CFO/finance ops | Product + implementation | High, data integration | Connectors, validation, UI |
| IT blueprint | Executive team | Advisory | Low code, high analysis | Research, documentation |
| Talent services | HR/project lead | Placement | Varies | N/A |
| SEVICO | Field operations | Project/product | Medium-high | Mobile/web features |

---

## 3. Which service line is most likely for a fresh graduate?

**Hypothesis:** Custom development or ERP implementation support, because:
- The ad lists general programming technologies.
- The company needs delivery capacity across client projects.
- Fresh graduates are economical for feature work, integration, testing, and documentation.
- The ad emphasises learning multiple stacks rather than one product.

**Alternative:** FOOMA product team, if the company is investing in product growth.

**How to handle in interview:** Express openness to both, with a preference grounded in evidence:
> "I enjoy end-to-end web development, and I am curious about enterprise integration. I would be happy to start where the delivery need is greatest, as long as there is mentoring and a clear learning path."

---

## 4. Business-case implications

If the case is about any of these services, use these lenses:

| If the case involves... | Emphasise... |
|---|---|
| ERP implementation | Process mapping, data migration, configuration vs. custom code, change management |
| Custom web app | Requirements, user roles, data model, API, security, testing |
| Finance automation | Data integrity, reconciliation, audit trail, exception handling |
| AI/computer vision | Accuracy, false positives, human review, operating conditions |
| Legacy modernisation | Incremental migration, backward compatibility, risk control |
| Talent platform | Matching logic, privacy, verification, scale |
| Field operations | Offline support, mobile UX, sync conflicts, photo evidence |

---

## 5. Questions to ask about products (only if relevant)

1. "Which service line is growing fastest for the team I would join?"
2. "Would a fresh graduate rotate across client projects or focus on one platform?"
3. "How does FOOMA's product roadmap interact with client customisation work?"
4. "What does success look like in the first six months?"

Ask one or two, not all.

---

## 6. Cross-references

- `technology_stack.md` — stack signals and preparation priorities.
- `projects_and_case_studies.md` — public project evidence.
- `../06_BUSINESS_CASES/` — case practice aligned to these service lines.
