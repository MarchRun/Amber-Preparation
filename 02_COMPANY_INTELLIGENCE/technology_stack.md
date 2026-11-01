# Technology Stack

**Purpose:** Separate what Amber actually uses from what third parties claim, and prioritise learning.
**Created:** 31 October 2026
**Last updated:** 31 October 2026
**Research status:** Public job ads and employee profiles only
**Confidence:** Low-medium for internal stack; high for advertised requirements

---

## 1. Evidence hierarchy

| Level | Meaning | Examples |
|---|---|---|
| A. Explicit in the Fresh Graduate Programmer ad | The company says it wants this | Java, PHP, Angular.js, .NET, Flutter, SQL |
| B. Explicit in other Amber job ads | Used somewhere in the company | Next.js, FastAPI, Python, AWS, C#, SAP, Oracle, Power Platform, Azure |
| C. Employee-reported | Individual team usage, may not be company standard | Laravel, CodeIgniter, Spring Boot, Vue.js, TypeScript, MySQL, JWT |
| D. Official service description | Platform/service context | Oracle, Odoo (Python/PostgreSQL), Dynamics 365, AI/computer vision, FOOMA |
| E. Inference | Logical but unconfirmed | REST APIs, Git, CI/CD, cloud hosting, relational databases |

---

## 2. Advertised requirements (Level A)

The archived **Fresh Graduate Programmer** ad lists:

- .NET
- Flutter
- Java
- Angular.js
- PHP

And states: "Interested in learning and developing applications using Java, PHP, Angular, .NET, and Flutter."

**Interpretation:**
- This is a **generalist** role, not a specialist frontend or backend role.
- The company expects willingness to learn multiple stacks, not existing mastery of all.
- The ad says "Angular.js" and also "Angular" in its description. AngularJS and modern Angular are different frameworks; which is intended is UNKNOWN. Ask neutrally rather than assume.
- .NET likely means C#/.NET web development, possibly with Dynamics/Power Platform.
- Flutter implies mobile development exposure.

**Critical:** The ad says "interested in learning," not "expert in." This gives permission to be honest about gaps.

---

## 3. Other Amber job-ad signals (Level B)

Across current and archived postings observed in October 2026:

| Technology | Context |
|---|---|
| Java / Spring Boot | Java Backend Developer, Fullstack Developer |
| PHP / Laravel / CodeIgniter | Fullstack, Programmer (.NET) adjacent roles |
| .NET / C# | Programmer (.NET), Technical Lead (.NET) |
| Angular | Fresh Graduate Programmer |
| Flutter | Fresh Graduate Programmer |
| Next.js | Full Stack Developer |
| FastAPI / Python | Full Stack Developer |
| AWS | Cloud Engineer |
| Microsoft 365 / Power Platform / Azure | Programmer (.NET) |
| SAP GRC / FICO | SAP consultant roles |
| Oracle / NetSuite / PeopleSoft | Oracle implementation roles |
| SQL Server / MySQL / PostgreSQL | Backend and full-stack roles |

**Interpretation:** The company runs multiple technology practices. A fresh graduate may be assigned based on project demand, not personal preference.

---

## 4. Employee-reported stack (Level C)

From public LinkedIn snippets:

**Idham Mansyah Awwalu — Fullstack Developer – Middle (Apr 2026–present)**
- Maintains and updates legacy programs
- Frontend internal CMS with Vue.js and TypeScript
- Backend/database with MySQL and Java Spring Boot
- Mobile apps with Flutter
- PHP (Laravel, CodeIgniter 3 & 4), REST API, JWT authentication
- Software architecture, Agile/Scrum

**Lo Ping An — Technical Lead Developer (since Jan 2021)**
- Technical leadership; prior senior programmer and consulting experience

**Rifky Safaryansyah — Frontend Developer (since Apr 2021)**
- Frontend development

**Winston Adinata Kusumo — Frontend Developer (Jul 2024–Jul 2026)**
- Frontend development; prior Blibli software engineering internship

**Caution:** These are self-reported profiles. They show what individuals do, not a company standard. Do not cite them by name in an interview.

---

## 5. Platform and service stack (Level D)

| Offering | Likely technologies | Confidence |
|---|---|---|
| Oracle implementation | Oracle E-Business Suite, Oracle Cloud, NetSuite, SQL, PL/SQL, integration tools | Medium |
| Odoo implementation | Python, PostgreSQL, Odoo ORM, XML views, JavaScript | High (Odoo is Python/PostgreSQL by definition) |
| Dynamics 365 | C#, .NET, Power Platform, Dataverse, Azure | Medium-high |
| Custom development | JavaScript/TypeScript, React/Next.js, Angular, PHP, Java, .NET, Flutter | Medium |
| FOOMA | Data integration, ETL, API connectors, workflow engine, web UI | Low (inferred) |
| Stockpile monitoring | Computer vision, photogrammetry, camera systems, dashboards | Low (inferred) |
| Cloud | AWS (advertised), Azure (Dynamics context), Google Cloud (employee/project history) | Medium |

---

## 6. What Marchel already has

| Skill | Evidence | Relevance |
|---|---|---|
| JavaScript / TypeScript | SMB Suvanna Dipa, Kibang, Iterary | Directly relevant to Angular/React/Next.js |
| React / Next.js | SMB Suvanna Dipa, Kibang | Frontend transferable to Angular |
| PHP / CodeIgniter | Bappenas internship, Simonika | Directly advertised |
| SQL / MySQL / PostgreSQL | Bappenas, SMB, Iterary | Directly advertised |
| Python | Academic/game projects | Transferable to Odoo/FastAPI |
| C++ | Academic | OOP transferable to Java/.NET |
| Docker / cloud | Iterary | Deployment awareness |
| Git / Jira / GitLab | Internship and projects | Team workflow |
| Supabase / Firebase | Projects | BaaS, auth, rapid development |
| Flutter | None | Gap |
| Java | No project or coursework evidence in supplied CV/portfolio | Gap; ask rather than infer coursework |
| .NET / C# | None | Gap |
| Angular | None | Gap |

---

## 7. Learning priority for 2 days

Do **not** try to learn four new stacks. Instead:

### Tier 1 — Must be able to discuss (today)
- Java vs. JavaScript: static typing, JVM, OOP, Spring Boot basics.
- .NET/C#: managed runtime, ASP.NET Core basics, NuGet.
- Angular: components, services, dependency injection, TypeScript.
- Flutter: widgets, Dart, single codebase, hot reload.
- SQL: joins, aggregation, subqueries, indexes, transactions.

### Tier 2 — Be able to map concepts (today)
- How Marchel's React knowledge transfers to Angular.
- How TypeScript/Node knowledge transfers to Java/.NET.
- How REST API design is language-agnostic.
- How relational data modelling is language-agnostic.

### Tier 3 — Ignore unless asked (do not study)
- Advanced Spring internals.
- Advanced .NET CLR tuning.
- Flutter state-management libraries.
- Oracle PL/SQL packages.
- SAP modules.

---

## 8. Transferable-concept table (use in answers)

| If asked about... | Bridge from Marchel's experience |
|---|---|
| Java | "I have used C++ and TypeScript with strong typing. Java's class model and Spring's controller-service-repository pattern are familiar concepts; I would need time to learn the ecosystem." |
| .NET | "I understand C# as a statically typed, managed language similar in role to Java. ASP.NET Core's middleware and dependency injection map to patterns I use in Node/Next.js." |
| Angular | "I build React/Next.js components with TypeScript. Angular's components, services, and RxJS are different, but the separation of UI and data logic is familiar." |
| Flutter | "I have not shipped a Flutter app. I understand it compiles Dart to native code and uses a widget tree, similar to component composition. I would start with a small CRUD app." |
| Oracle/Odoo | "I have not configured an ERP. I understand the data-integrity and process-mapping challenges from building role-based internal systems." |

**Rule:** Always add what you would do to close the gap. Do not stop at "I don't know."

---

## 9. Likely interview questions about stack

1. "Which language are you strongest in, and why?"
2. "You have not used Java. How would you approach a Java project?"
3. "What is the difference between Angular and React?"
4. "How would you learn .NET in your first month?"
5. "What does 'basic programming concepts' mean to you?"
6. "How comfortable are you with SQL beyond simple queries?"
7. "Have you worked with mobile development?"
8. "How do you decide which technology to use for a new project?"

Prepare one honest, structured answer for each. See `../08_QUESTION_BANK/04_programming_fundamentals.md` and `../07_ENGLISH_PREPARATION/technical_communication.md`.

---

## 10. Source anchors

- Fresh Graduate Programmer ad: https://glints.com/id/en/opportunities/jobs/fresh-graduate-programmer/57dc25b6-6867-4088-bc74-01e7b157a967
- Programmer (.NET) ad: https://glints.com/id/en/opportunities/jobs/programmer-net/54f86e05-1a8f-492d-a778-74564941f3b4
- Java Backend Developer ad: https://glints.com/id/en/opportunities/jobs/java-backend-developer/b6c14445-d52d-4703-8aeb-235cfbf1f0f5
- Official Solutions: https://www.ambersof.com/en/solutions
- LinkedIn company page: https://www.linkedin.com/company/ambersof

Retrieved 31 October 2026. Job ads may be closed or changed.
