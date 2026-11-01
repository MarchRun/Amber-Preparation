# 03 — CV and Project Deep Dive

**Purpose:** Survive the questions that separate candidates with similar CVs: what you actually owned, why you chose it, and what is wrong with it.
**Created:** 31 October 2026
**Items:** 10 (CV-01 … CV-10)
**Schema:** `_SCHEMA.md`
**Candidate for:** Marchel Karuna Kwee — PT Amber Solusi Internasional, Fresh Graduate Programmer, 2 November 2026

**Difficulty mix:** Foundation 4 · Intermediate 4 · Advanced 2

**Grounding:** Primary CV/portfolio overrides interpretation. Bappenas and Simonika are separate CV entries; whether they describe the same system is UNKNOWN. No particular bug, permission-layer implementation, schema decision or missing automated tests is evidenced. Proposed designs below are not past implementation claims.

---

### Q-CV-01 — SMB Suvanna Dipa, end to end

| Field | Value |
|---|---|
| **Category** | CV & Project Deep Dive |
| **Sub-skill** | Project ownership |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | Walk me through SMB Suvanna Dipa. What was the problem, what did you build, and what was yours? |
| **Pertanyaan (ID)** | Jelaskan SMB Suvanna Dipa. Apa masalahnya, apa yang Anda bangun, dan bagian mana yang benar-benar Anda kerjakan? |
| **What is assessed** | Whether you can describe a system from the user's problem down to your own contribution. |
| **Evidence basis** | Fact sheet §3.1 (Sunday school digitalisation; student/mentor/admin; Next.js, TypeScript, PostgreSQL, Supabase, Figma; RFID attendance integration). |
| **Strong answer outline** | School administration; documented role/stack; student/mentor/admin requirements; RFID integration; verify actual workflow details. |
| **Model answer (EN)** | SMB Suvanna Dipa is a Sunday school administration web application. My role was full-stack developer using Next.js, TypeScript, PostgreSQL and Supabase, with Figma listed for design. I developed and maintained operational features for student, mentor and admin requirements and integrated RFID attendance with the application. Those responsibilities are documented. I would explain the actual workflow from memory or code rather than invent the school's earlier bookkeeping process, and I would not claim the hardware contribution. |
| **Contoh jawaban (ID)** | SMB Suvanna Dipa merupakan aplikasi web administrasi sekolah minggu. Saya berperan sebagai full-stack developer dengan Next.js, TypeScript, PostgreSQL dan Supabase, serta Figma untuk desain. Saya membangun serta memelihara fitur operasional bagi kebutuhan siswa, mentor dan admin, lalu mengintegrasikan absensi RFID dengan aplikasi. Tanggung jawab itu terdokumentasi. Alur sebenarnya perlu dijelaskan dari ingatan atau kode, bukan dengan mengarang pembukuan sekolah sebelumnya, dan saya tidak mengklaim kontribusi perangkat keras. |
| **Follow-up** | Why three roles instead of one admin role and a simple list? |
| **Weak answer / red flag** | Describing features but never the problem; or claiming the RFID hardware, the IoT side, or the whole system as yours. |
| **Scoring anchor** | 1 = feature list with no problem or ownership boundary · 3 = clear description but vague on what was yours · 5 = problem, model, stack rationale, integration, and an explicit boundary, all in order |

---

### Q-CV-02 — Bappenas backend work

| Field | Value |
|---|---|
| **Category** | CV & Project Deep Dive |
| **Sub-skill** | Professional experience |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | Your Bappenas internship is dated June–July 2025. What could you realistically contribute during that period? |
| **Pertanyaan (ID)** | Magang Bappenas Anda tercatat Juni–Juli 2025. Apa kontribusi realistis selama periode itu? |
| **What is assessed** | Whether you can describe short experience accurately without inflating it. |
| **Evidence basis** | CV p1 and portfolio p3; exact dates within Jun–Jul and review policy UNKNOWN. |
| **Strong answer outline** | Backend features; four documented team roles; institutional alignment; no automatic review/deployment claim. |
| **Model answer (EN)** | I contributed backend features rather than claim full-system architecture ownership. I used PHP, CodeIgniter and MySQL in a four-person internship team, alongside project management, analysis and frontend roles. My responsibilities included business logic aligned with institutional workflows and coordination with cross-department stakeholders. Jira, GitLab and Agile development are documented. The exact branch, review and deployment process needs confirmation, so I would describe it only from an actual example I can explain. |
| **Contoh jawaban (ID)** | Saya berkontribusi pada fitur backend, bukan mengklaim kepemilikan arsitektur seluruh sistem. Saya memakai PHP, CodeIgniter dan MySQL dalam tim magang empat orang bersama peran manajemen proyek, analisis dan frontend. Tugas saya mencakup logika bisnis sesuai alur institusi serta koordinasi lintas departemen. Jira, GitLab dan Agile tercatat dalam dokumen. Proses branch, review dan deployment yang tepat perlu dikonfirmasi dan hanya saya jelaskan dari contoh nyata yang dapat diterangkan. |
| **Follow-up** | What did the system analyst give you, and what did you still have to work out yourself? |
| **Weak answer / red flag** | Inflating a one-month internship into "I designed the architecture" or "I deployed it to production"; or being unable to name what you personally built. |
| **Scoring anchor** | 1 = inflated scope claims · 3 = accurate but thin, no process detail · 5 = calibrated scope, named team roles, the nature of the logic, and a specific lesson about requirements |

---

### Q-CV-03 — Iterary deployment

| Field | Value |
|---|---|
| **Category** | CV & Project Deep Dive |
| **Sub-skill** | Deployment and operations |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | You list cloud and deployment work on Iterary. What did you actually set up, step by step? |
| **Pertanyaan (ID)** | Anda mencantumkan pekerjaan cloud dan deployment di Iterary. Apa saja yang benar-benar Anda siapkan, langkah demi langkah? |
| **What is assessed** | Whether the deployment claim is operational knowledge or a keyword. |
| **Evidence basis** | Fact sheet §3.3 (React PWA; MySQL, Redis, Docker, Google Cloud, JavaScript; server setup, automated deployment workflow, traffic routing). |
| **Strong answer outline** | Library PWA; cloud role; documented deployment/automation/routing; confirm actual topology and Redis use. |
| **Model answer (EN)** | Iterary is a library management PWA, and my documented role was cloud engineer. I configured the cloud server environment, application deployment and supporting services, established an automated deployment workflow and configured web traffic routing. The project stack lists React, MySQL, Docker, Redis and Google Cloud. I would describe the exact configuration from the real project artifacts. The documents do not establish a specific topology or Redis purpose, and I should not add Kubernetes or multi-region expertise. |
| **Contoh jawaban (ID)** | Iterary merupakan PWA manajemen perpustakaan, dengan peran saya yang tercatat sebagai cloud engineer. Saya mengonfigurasi lingkungan server, deployment aplikasi dan layanan pendukung, menyiapkan alur deployment otomatis serta routing trafik web. Stack proyek mencantumkan React, MySQL, Docker, Redis dan Google Cloud. Konfigurasi tepatnya harus dijelaskan dari artefak asli. Dokumen tidak menetapkan topologi atau kegunaan Redis tertentu, dan saya tidak boleh menambah klaim Kubernetes maupun keahlian multi-region. |
| **Follow-up** | What happened the first time you deployed, and what broke? |
| **Weak answer / red flag** | Claiming Kubernetes, Terraform, or multi-region architecture; or saying "I deployed it" with no idea what the deployment consisted of. |
| **Scoring anchor** | 1 = keyword claims with no steps · 3 = correct components described loosely · 5 = ordered steps, the purpose of each service, and a voluntary statement of what was not built |

---

### Q-CV-04 — Kibang as project manager

| Field | Value |
|---|---|
| **Category** | CV & Project Deep Dive |
| **Sub-skill** | Planning and documentation |
| **Difficulty** | Foundation |
| **Asked in** | HR screen or technical |
| **Question (EN)** | You were project manager on Kibang. What does a student project manager actually do? |
| **Pertanyaan (ID)** | Anda menjadi project manager di Kibang. Sebenarnya apa yang dikerjakan project manager mahasiswa? |
| **What is assessed** | Whether you can describe planning work concretely rather than as a title. |
| **Evidence basis** | Fact sheet §3.4 (IoT soil monitoring for village conditions: pH, temperature, moisture; Next.js, JavaScript, Firebase; led planning; specifications, budget, risks, testing documentation; contributed frontend, database integration, sensor testing). |
| **Strong answer outline** | • What the system was and who needed it<br>• Planning: scope, sequence, who does what<br>• Documents: specification, budget, risk list, test plan<br>• Still an engineer: frontend, database integration, sensor testing<br>• What the role actually taught |
| **Model answer (EN)** | Kibang was an IoT-based monitoring system for village soil conditions — pH, temperature, and moisture — built with Next.js, JavaScript, and Firebase. As project manager I owned the planning side: what was in scope, in what order we would build it, who was doing which part, and what could go wrong. I prepared the specification, the budget, the risk list, and the testing documentation. I was not only managing, though. I contributed to the frontend, the database integration, and the sensor testing, which meant I could not plan work I did not understand. |
| **Contoh jawaban (ID)** | Kibang adalah sistem pemantauan berbasis IoT untuk kondisi tanah desa — pH, suhu, dan kelembapan — dibangun dengan Next.js, JavaScript, dan Firebase. Sebagai project manager saya memegang sisi perencanaan: apa yang masuk lingkup, urutan pengerjaan, siapa mengerjakan bagian mana, dan apa yang bisa salah. Saya menyiapkan spesifikasi, anggaran, daftar risiko, dan dokumentasi pengujian. Tetapi saya tidak hanya mengelola. Saya ikut mengerjakan frontend, integrasi basis data, dan pengujian sensor, sehingga saya tidak mungkin merencanakan pekerjaan yang tidak saya pahami. |
| **Follow-up** | Show me how you wrote a risk in that document — what did one look like? |
| **Weak answer / red flag** | Presenting the title as authority ("I led the team") without naming what you produced; or claiming you wrote the embedded firmware. |
| **Scoring anchor** | 1 = title only, no artefacts · 3 = lists documents without linking them to decisions · 5 = names the artefacts, how they were used, and keeps a technical contribution in the story |

---

### Q-CV-05 — Simonika and SOPs

| Field | Value |
|---|---|
| **Category** | CV & Project Deep Dive |
| **Sub-skill** | Requirements fidelity |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | Tell me about Simonika. What does "implementing based on SOPs" mean in practice? |
| **Pertanyaan (ID)** | Ceritakan tentang Simonika. Apa arti "mengimplementasikan berdasarkan SOP" dalam praktik? |
| **What is assessed** | Whether you understand that SOP-driven work constrains design, and whether you keep Simonika distinct from Bappenas. |
| **Evidence basis** | Fact sheet §3.2 (internal ICT infrastructure monitoring; PHP, CodeIgniter, MySQL, Jira, GitLab; departmental requirements and SOPs; backend workflows connecting frontend to database operations). Simonika is listed separately from the Bappenas internship. |
| **Strong answer outline** | ICT monitoring; backend responsibilities; departmental requirements/SOPs; actual rule example; internship relationship unresolved. |
| **Model answer (EN)** | Simonika is listed as an internal ICT infrastructure monitoring project. My backend responsibilities included implementing departmental requirements and SOPs, connecting frontend workflows to database operations and managing organisational data. PHP, CodeIgniter, MySQL, Jira and GitLab are listed. I would explain a particular SOP rule from the actual project rather than invent its sequence. The CV lists Simonika and the Bappenas internship separately, but that does not prove they describe different systems; I need to confirm the relationship. |
| **Contoh jawaban (ID)** | Simonika tercatat sebagai proyek pemantauan infrastruktur TIK internal. Tanggung jawab backend saya mencakup implementasi kebutuhan departemen dan SOP, penghubungan alur frontend ke operasi basis data serta pengelolaan data organisasi. PHP, CodeIgniter, MySQL, Jira dan GitLab tercantum. Aturan SOP tertentu perlu dijelaskan dari proyek asli, bukan dengan mengarang urutannya. Simonika dan magang Bappenas ditulis sebagai entri berbeda, tetapi itu belum membuktikan sistemnya berbeda; hubungannya perlu saya konfirmasi. |
| **Follow-up** | Was there a moment where the SOP was wrong and you had to say so? |
| **Weak answer / red flag** | Asserting Simonika is the same as, or different from, the internship system without confirmation; inventing SOP changes or production status. |
| **Scoring anchor** | 1 = conflates it with Bappenas or invents scope · 3 = accurate description of the stack and task · 5 = explains what the constraint changed about the design and keeps the two items separate |

---

### Q-CV-06 — A technical decision you made

| Field | Value |
|---|---|
| **Category** | CV & Project Deep Dive |
| **Sub-skill** | Design judgement |
| **Difficulty** | Advanced |
| **Asked in** | Technical |
| **Question (EN)** | Tell me about a technical decision that was genuinely yours, and why you made it that way. |
| **Pertanyaan (ID)** | Ceritakan keputusan teknis yang benar-benar Anda ambil sendiri, dan mengapa Anda memilihnya. |
| **What is assessed** | Whether you can defend a trade-off with reasoning rather than naming a popular tool. |
| **Evidence basis** | Fact sheet §3.1 (PostgreSQL and Supabase; three roles; RFID attendance), §6.4 (joins and relational modelling). |
| **Strong answer outline** | Supply an actual owned decision; alternative and constraint; supported result; hypothetical design clearly separated. |
| **Model answer (EN)** | The documents establish PostgreSQL use, not who chose it or which alternatives were evaluated. I need a real decision I personally owned before answering this as history. As hypothetical reasoning, I would favour a relational model when attendance depends on students, sessions and reporting relationships, because keys and transactions can enforce important rules. I would compare maintenance and access needs with alternatives, but I should not claim that comparison happened in my project without confirmation. |
| **Contoh jawaban (ID)** | Dokumen membuktikan penggunaan PostgreSQL, bukan siapa yang memilihnya atau alternatif apa yang dinilai. Saya memerlukan keputusan asli yang benar-benar saya ambil sebelum menjawab sebagai pengalaman. Secara hipotetis, saya memilih model relasional ketika absensi bergantung pada siswa, sesi dan hubungan laporan, karena kunci serta transaksi menjaga aturan penting. Kebutuhan pemeliharaan dan akses dibandingkan dengan alternatif, tetapi saya tidak mengklaim perbandingan itu terjadi di proyek tanpa konfirmasi. |
| **Follow-up** | When would a document store have been the right call? |
| **Weak answer / red flag** | "I used PostgreSQL because it is popular"; or claiming the decision was made by someone else while presenting it as yours. |
| **Scoring anchor** | 1 = technology name with no reasoning · 3 = a real reason but no cost · 5 = names the decision, the alternative, the cost, the benefit, and what would change the answer |

---

### Q-CV-07 — A limitation of your project

| Field | Value |
|---|---|
| **Category** | CV & Project Deep Dive |
| **Sub-skill** | Critical evaluation |
| **Difficulty** | Advanced |
| **Asked in** | Technical |
| **Question (EN)** | What is the weakest part of the system you are most proud of? |
| **Pertanyaan (ID)** | Apa bagian terlemah dari sistem yang paling Anda banggakan? |
| **What is assessed** | Whether you can critique your own work precisely, and whether you know the difference between testing and hoping. |
| **Evidence basis** | Fact sheet §7 (testing: "tested features and prepared testing documentation", not automated strategy), §3.1. |
| **Strong answer outline** | Actual limitation requires verification; proposed audit of permissions/retries/tests; do not infer missing tests from omitted CV detail. |
| **Model answer (EN)** | I would need to inspect the actual project before naming its weakest part. My documents do not establish automated test coverage, validation data or operational scale, so I should not claim there was no test suite. A useful proposed review would examine permission boundaries, duplicate attendance and recovery behaviour. After that review, I could identify a real limitation, explain its impact and propose the first fix with evidence rather than invent a weakness for the interview. |
| **Contoh jawaban (ID)** | Saya perlu memeriksa proyek asli sebelum menyebut bagian terlemahnya. Dokumen tidak menetapkan cakupan pengujian otomatis, data validasi atau skala operasional, sehingga saya tidak boleh mengklaim tidak ada test suite. Pemeriksaan usulan yang berguna mencakup batas izin, duplikasi absensi dan pemulihan. Sesudah review, saya dapat menyebut keterbatasan nyata, menjelaskan dampak dan mengusulkan perbaikan pertama berdasarkan bukti, bukan mengarang kelemahan untuk wawancara. |
| **Follow-up** | What is the first test you would write, specifically? |
| **Weak answer / red flag** | "There are no weaknesses, it works"; or listing only external limitations such as "no budget" instead of a technical judgement. |
| **Scoring anchor** | 1 = denies weakness or blames others · 3 = admits weak testing in general terms · 5 = names the specific fragility, explains how it would surface, and states the first fix |

---

### Q-CV-08 — What you would rebuild

| Field | Value |
|---|---|
| **Category** | CV & Project Deep Dive |
| **Sub-skill** | Reflective design |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | Take any project on your CV. What would you rebuild, and what would you keep exactly as it is? |
| **Pertanyaan (ID)** | Ambil salah satu proyek di CV Anda. Apa yang akan Anda bangun ulang, dan apa yang tetap Anda pertahankan? |
| **What is assessed** | Whether you can separate a better design from a different one, and whether you protect what worked. |
| **Evidence basis** | Fact sheet §3.3 (Iterary: server setup, Docker, automated deployment, traffic routing). |
| **Strong answer outline** | • Project: Iterary deployment<br>• Rebuild: the environment defined in a file, not in my memory<br>• Add: a staging environment before production<br>• Keep: the container approach and the automated deploy path<br>• Why: reproducibility beats a clever one-off setup |
| **Model answer (EN)** | Iterary gives me a documented deployment area to review. My role included cloud setup, automated deployment and traffic routing, with Docker in the stack. I would inspect reproducibility, environment separation and recovery instructions before recommending a rebuild. If a gap exists, I would improve that specific part while keeping useful automation. This is a proposed review, not evidence that the original environment existed only in my head or lacked staging. |
| **Contoh jawaban (ID)** | Iterary memberi bagian deployment yang terdokumentasi untuk ditinjau. Peran saya mencakup penyiapan cloud, deployment otomatis dan routing trafik, dengan Docker pada stack. Saya memeriksa reproduktibilitas, pemisahan lingkungan dan instruksi pemulihan sebelum mengusulkan pembangunan ulang. Jika ditemukan celah, bagian itu diperbaiki sambil mempertahankan otomatisasi yang berguna. Ini usulan pemeriksaan, bukan bukti bahwa lingkungan lama hanya ada dalam ingatan atau belum mempunyai staging. |
| **Follow-up** | What would that cost you in the first week, and is it worth it? |
| **Weak answer / red flag** | "I would rebuild everything with a modern framework" with no reason; or being unable to name anything you would keep. |
| **Scoring anchor** | 1 = rebuilds for novelty · 3 = one improvement with a plausible reason · 5 = names the failure mode, a specific change, a cost, and protects the parts that worked |

---

### Q-CV-09 — Code you are proud of

| Field | Value |
|---|---|
| **Category** | CV & Project Deep Dive |
| **Sub-skill** | Code quality |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | Show me, or describe, a piece of code you are proud of. Not the biggest — the one you think is well made. |
| **Pertanyaan (ID)** | Tunjukkan atau jelaskan kode yang Anda banggakan. Bukan yang terbesar, tetapi yang menurut Anda dibuat dengan baik. |
| **What is assessed** | Whether your standard of "good code" goes beyond "it runs". |
| **Evidence basis** | Fact sheet §3.1 (student/mentor/admin roles; attendance records from RFID), §6.1. |
| **Strong answer outline** | Choose actual code; explain requirement/invariant/readability/test; acknowledge real limit; no invented permission layer. |
| **Model answer (EN)** | I should choose an actual code sample before giving this answer. The portfolio documents full-stack and backend responsibilities, but it does not show a specific permission layer or prove its test coverage. I would explain the sample's requirement, the invariant it protects, why the names and boundaries are clear and how I verified it. If I only have a proposed example, I would label it as a design exercise rather than code I already wrote. |
| **Contoh jawaban (ID)** | Saya harus memilih sampel kode asli sebelum menjawab. Portofolio mendokumentasikan tanggung jawab full-stack dan backend, tetapi tidak menunjukkan lapisan izin tertentu atau membuktikan cakupan pengujiannya. Saya menjelaskan kebutuhan sampel, aturan yang dijaga, kejelasan nama serta batas komponen dan cara verifikasinya. Jika contoh yang tersedia baru berupa usulan, saya menandainya sebagai latihan desain, bukan kode yang sudah pernah saya tulis. |
| **Follow-up** | What would a senior developer change about it first? |
| **Weak answer / red flag** | Describing a whole project instead of a piece; or defining quality only as "it works and looks neat". |
| **Scoring anchor** | 1 = cannot name a specific piece · 3 = names something but judges it only on readability · 5 = a specific component, a design principle, evidence it survived change, and a known weakness |

---

### Q-CV-10 — A bug you fixed

| Field | Value |
|---|---|
| **Category** | CV & Project Deep Dive |
| **Sub-skill** | Debugging |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | Tell me about a bug that took you longer than it should have. How did you find it? |
| **Pertanyaan (ID)** | Ceritakan bug yang Anda selesaikan lebih lama dari seharusnya. Bagaimana Anda menemukannya? |
| **What is assessed** | Whether you debug by method — reproduce, narrow, verify — or by changing things until it stops. |
| **Evidence basis** | UNKNOWN: no specific defect or debugging incident is recorded in CV/portfolio. |
| **Strong answer outline** | Supply real bug; expected/actual; reproduction/evidence; correction; regression; hypothetical method if none ready. |
| **Model answer (EN)** | I need a real bug example to answer this as personal experience. My documents record RFID integration but no particular defect. As a hypothetical method, I would reproduce a known input, trace the payload through validation and the write path, test one hypothesis and add a regression check. I would separate what I observed from what I assumed. I should not claim a specific RFID mismatch happened just because that boundary is plausible. |
| **Contoh jawaban (ID)** | Saya memerlukan contoh bug asli untuk menjawab sebagai pengalaman pribadi. Dokumen mencatat integrasi RFID, tetapi tidak menyebut cacat tertentu. Sebagai metode hipotetis, saya mereproduksi input yang diketahui, menelusuri payload melalui validasi dan penyimpanan, menguji satu hipotesis lalu menambah pemeriksaan regresi. Pengamatan dipisahkan dari asumsi. Saya tidak boleh mengklaim ketidakcocokan RFID tertentu pernah terjadi hanya karena masalah di batas itu terdengar masuk akal. |
| **Follow-up** | How would you have caught that before a user saw it? |
| **Weak answer / red flag** | A story with no diagnosis ("I just changed things until it worked"); or a bug that turns out to be someone else's fault. |
| **Scoring anchor** | 1 = trial and error with no method · 3 = clear symptom and fix, thin diagnosis · 5 = reproduce, isolate, correct the assumption, and a generalised lesson about where your bugs occur |
