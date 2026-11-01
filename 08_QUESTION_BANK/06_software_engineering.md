# 06 — Software Engineering

**Purpose:** Fifteen original bilingual questions about delivery practice.
**Created / last updated:** 31 October 2026
**Status:** General-knowledge/proposed answers. Past team practices must be confirmed; practice scoring is not Amber's rubric.
**Schema:** `_SCHEMA.md`

### Q-SE-01 — SDLC

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Lifecycle |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | What happens before and after implementation in the SDLC? |
| **Pertanyaan (ID)** | Apa yang dilakukan sebelum dan sesudah implementasi dalam SDLC? |
| **What is assessed** | Engineering beyond writing code. |
| **Evidence basis** | General knowledge. |
| **Strong answer outline** | Understand need; agree requirements; design; verify; release; maintain. |
| **Model answer (EN)** | Before implementation I would understand the problem, identify users and constraints, agree acceptance criteria and choose a suitable design. Afterwards I would verify behaviour, release safely and observe how it works in use. Maintenance and feedback can change the requirements again. I see the lifecycle as a feedback process, not a rule that testing and learning begin only after all coding has finished. |
| **Contoh jawaban (ID)** | Sebelum implementasi saya memahami masalah, pengguna dan batasan, menyepakati kriteria penerimaan, lalu memilih desain yang sesuai. Sesudahnya saya memverifikasi perilaku, merilis dengan aman dan mengamati penggunaan. Pemeliharaan serta umpan balik bisa mengubah kebutuhan kembali. SDLC saya pahami sebagai proses dengan umpan balik, bukan aturan bahwa pengujian dan pembelajaran baru dimulai setelah seluruh kode selesai ditulis. |
| **Follow-up** | Where would you check whether the feature solves the original problem? |
| **Weak answer / red flag** | Describes only design, code and delivery with no validation. |
| **Scoring anchor** | 1 = code only · 3 = lifecycle stages · 5 = feedback and acceptance tied to outcome |

### Q-SE-02 — Requirements

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Functional / non-functional |
| **Difficulty** | Foundation |
| **Asked in** | Technical / business case |
| **Question (EN)** | Give one functional and one non-functional requirement for attendance. |
| **Pertanyaan (ID)** | Berikan satu kebutuhan fungsional dan nonfungsional untuk absensi. |
| **What is assessed** | Behaviour versus measurable quality constraints. |
| **Evidence basis** | Hypothetical attendance design. |
| **Strong answer outline** | Actor/action; quality constraint; measurable target needs agreement. |
| **Model answer (EN)** | A functional requirement could be that an assigned mentor can correct attendance with a reason. A non-functional requirement could limit report response time at an agreed concurrent load. I would agree the actual numbers with the stakeholder instead of inventing them. Security requirements also need concrete checks, such as rejecting access to another class, rather than simply saying the system must be secure. |
| **Contoh jawaban (ID)** | Kebutuhan fungsionalnya misalnya mentor yang ditugaskan dapat mengoreksi absensi dengan alasan. Kebutuhan nonfungsionalnya dapat membatasi waktu respons laporan pada beban bersamaan yang disepakati. Angka target harus disetujui pemangku kepentingan, bukan saya karang. Persyaratan keamanan juga memerlukan pemeriksaan nyata, seperti menolak akses ke kelas lain, bukan sekadar menyatakan bahwa sistem harus aman. |
| **Follow-up** | How would you verify your non-functional requirement? |
| **Weak answer / red flag** | Gives vague labels such as fast, secure and user-friendly only. |
| **Scoring anchor** | 1 = confuses requirement types · 3 = correct examples · 5 = observable verification and agreed targets |

### Q-SE-03 — Acceptance criteria

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Testable scope |
| **Difficulty** | Foundation |
| **Asked in** | Business case / technical |
| **Question (EN)** | How do acceptance criteria differ from a feature title? |
| **Pertanyaan (ID)** | Apa perbedaan kriteria penerimaan dan judul fitur? |
| **What is assessed** | Converting vague work into verifiable behaviour. |
| **Evidence basis** | General knowledge. |
| **Strong answer outline** | Title is intent; criteria define conditions; happy and denied paths. |
| **Model answer (EN)** | A title such as attendance correction tells me the topic, but not when the work is accepted. I would specify who can correct which records, required input, the resulting history and the rejection conditions. For example, an assigned mentor can correct an open session with a reason, while an unassigned mentor is denied. Those criteria guide implementation, review and stakeholder verification. |
| **Contoh jawaban (ID)** | Judul seperti koreksi absensi hanya menyebut topik, belum menjelaskan kapan pekerjaan diterima. Saya menentukan siapa boleh mengoreksi catatan mana, input wajib, riwayat yang dihasilkan dan kondisi penolakannya. Contohnya, mentor yang ditugaskan dapat mengoreksi sesi terbuka dengan alasan, sedangkan mentor lain ditolak. Kriteria tersebut menjadi acuan implementasi, pemeriksaan kode dan verifikasi oleh pemangku kepentingan. |
| **Follow-up** | What acceptance criterion covers concurrent corrections? |
| **Weak answer / red flag** | Treats "the page exists" as sufficient acceptance. |
| **Scoring anchor** | 1 = vague completion · 3 = testable happy path · 5 = permissions, errors and state boundaries |

### Q-SE-04 — Agile evidence

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Process accuracy |
| **Difficulty** | Foundation |
| **Asked in** | Technical / HR |
| **Question (EN)** | Does using Jira mean a team is Agile or Scrum? |
| **Pertanyaan (ID)** | Apakah penggunaan Jira berarti tim sudah menjalankan Agile atau Scrum? |
| **What is assessed** | Distinguishing tools from process. |
| **Evidence basis** | CV documents Agile, Jira and GitLab; exact ceremonies unknown. |
| **Strong answer outline** | Tool not process; feedback/adaptation; Scrum specifics; evidence boundary. |
| **Model answer (EN)** | No. Jira can support many workflows; the tool does not prove that feedback and adaptation happen. Scrum also has specific accountabilities, events and artifacts. My CV records an Agile internship with Jira and GitLab, but it does not document every Scrum ceremony. I would describe the practices I actually remember rather than assume the full framework from the software we used. |
| **Contoh jawaban (ID)** | Tidak. Jira mendukung banyak alur kerja; alat tersebut tidak membuktikan bahwa tim benar-benar memakai umpan balik dan adaptasi. Scrum juga mempunyai tanggung jawab, acara dan artefak tertentu. CV saya menyebut magang dengan Agile, Jira dan GitLab, tetapi tidak merinci seluruh acara Scrum. Saya akan menjelaskan praktik yang benar-benar saya ingat, bukan menyimpulkan satu kerangka lengkap hanya dari alat yang digunakan. |
| **Follow-up** | Which real team practice can you explain from the internship? |
| **Weak answer / red flag** | Invents sprints, standups or reviews because Jira is listed. |
| **Scoring anchor** | 1 = tool equals process · 3 = distinguishes them · 5 = accurate framework and evidence boundary |

### Q-SE-05 — Merge and rebase

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Git collaboration |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | What is the practical difference between merging and rebasing? |
| **Pertanyaan (ID)** | Apa perbedaan praktis merge dan rebase? |
| **What is assessed** | History semantics and safe teamwork. |
| **Evidence basis** | General knowledge; no specific internship branching policy documented. |
| **Strong answer outline** | Combine histories; replay commits; changed IDs; shared-branch caution. |
| **Model answer (EN)** | Merge combines histories and may create a merge commit, while rebase replays commits onto another base and changes their identities. I would follow the team's history policy rather than treat one as always better. Rebasing a private branch can simplify its history, but rewriting a shared branch can disrupt teammates. Before either operation I would understand the changes and handle conflicts by preserving intended behaviour, not blindly selecting one side. |
| **Contoh jawaban (ID)** | Merge menggabungkan riwayat dan dapat membuat merge commit, sedangkan rebase memutar ulang commit di atas basis lain sehingga identitasnya berubah. Saya mengikuti kebijakan tim, bukan menganggap salah satunya selalu lebih baik. Rebase cabang pribadi dapat merapikan riwayat, tetapi menulis ulang cabang bersama bisa mengganggu rekan. Konflik harus diselesaikan dengan memahami perilaku yang diinginkan, bukan memilih satu sisi secara membabi buta. |
| **Follow-up** | How would you verify a conflict resolution? |
| **Weak answer / red flag** | Recommends force-pushing over shared work without agreement. |
| **Scoring anchor** | 1 = unsafe history rewrite · 3 = correct definitions · 5 = collaboration policy and behavioural verification |

### Q-SE-06 — Test levels

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Testing strategy |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | How do unit, integration and E2E tests complement each other? |
| **Pertanyaan (ID)** | Bagaimana unit, integration dan E2E test saling melengkapi? |
| **What is assessed** | Choosing tests by risk and boundary. |
| **Evidence basis** | General knowledge; candidate automated coverage is unknown. |
| **Strong answer outline** | Isolated logic; real boundaries; user workflow; cost/feedback. |
| **Model answer (EN)** | Unit tests give fast feedback on small logic, integration tests verify boundaries such as database constraints, and E2E tests exercise an important user workflow. I would use each where it catches a meaningful risk, not target a fashionable ratio. A mocked repository cannot prove a real foreign key works, while testing every arithmetic rule through the browser would make feedback slow and failures harder to diagnose. |
| **Contoh jawaban (ID)** | Unit test memberi umpan balik cepat untuk logika kecil, integration test memeriksa batas seperti constraint basis data, dan E2E test menjalankan alur pengguna penting. Saya memakai masing-masing sesuai risiko yang perlu ditangkap, bukan mengejar rasio populer. Repository yang dimock tidak membuktikan foreign key nyata bekerja, sedangkan menguji setiap aturan hitung melalui browser membuat umpan balik lambat dan sumber kegagalan lebih sulit ditemukan. |
| **Follow-up** | Which level should catch duplicate attendance records? |
| **Weak answer / red flag** | Claims 100% unit coverage proves the whole system works. |
| **Scoring anchor** | 1 = confuses levels · 3 = correct definitions · 5 = risk-based examples and mock limitations |

### Q-SE-07 — Review request

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Code review |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | What should a useful pull or merge request contain? |
| **Pertanyaan (ID)** | Apa isi pull request atau merge request yang membantu peninjau? |
| **What is assessed** | Making changes reviewable and verifiable. |
| **Evidence basis** | Proposed workflow; no exact candidate review policy established. |
| **Strong answer outline** | Purpose; scope; tests; risks; migration; small coherent diff. |
| **Model answer (EN)** | I would explain the problem, the chosen approach and the exact scope of the change. I would include test evidence, relevant screenshots or examples, migration requirements and known risks. A small coherent diff is easier to review than unrelated refactoring mixed with a fix. I would also tell the reviewer which decision needs attention, rather than expect them to reconstruct the requirement from the code alone. |
| **Contoh jawaban (ID)** | Saya menjelaskan masalah, pendekatan dan lingkup perubahan secara tepat. Saya menyertakan bukti pengujian, contoh atau tangkapan layar yang relevan, kebutuhan migrasi dan risiko yang diketahui. Diff kecil yang koheren lebih mudah diperiksa daripada perbaikan yang dicampur refactor tidak terkait. Saya juga menunjukkan keputusan mana yang perlu diperhatikan peninjau, bukan berharap kebutuhan bisnis dapat ditebak hanya dari kode. |
| **Follow-up** | What would make you split one request into two? |
| **Weak answer / red flag** | Gives only "fixed bug" with no test evidence. |
| **Scoring anchor** | 1 = opaque diff · 3 = purpose and tests · 5 = coherent scope, risk and review focus |

### Q-SE-08 — Estimate uncertainty

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Estimation |
| **Difficulty** | Intermediate |
| **Asked in** | Business case / HR |
| **Question (EN)** | How would you estimate a feature when an external API is unfamiliar? |
| **Pertanyaan (ID)** | Bagaimana memperkirakan pekerjaan ketika API eksternal belum dikenal? |
| **What is assessed** | Managing uncertainty without false precision. |
| **Evidence basis** | Hypothetical approach. |
| **Strong answer outline** | Identify unknowns; timeboxed spike; dependency; range/checkpoint. |
| **Model answer (EN)** | I would separate what I understand from the integration unknowns, such as authentication, limits and failure behaviour. I would propose a short investigation using the actual contract and a safe test environment, then revise the estimate. I would give a range with assumptions and identify dependencies on credentials or vendor support. A precise date before those checks would look confident but would not be a reliable commitment. |
| **Contoh jawaban (ID)** | Saya memisahkan pekerjaan yang dipahami dari ketidakpastian integrasi, seperti autentikasi, batas penggunaan dan perilaku kegagalan. Saya mengusulkan investigasi singkat memakai kontrak nyata dan lingkungan uji aman, lalu memperbarui perkiraan. Saya memberi rentang dengan asumsi serta ketergantungan pada kredensial atau dukungan vendor. Tanggal pasti sebelum pemeriksaan itu mungkin terlihat percaya diri, tetapi belum merupakan komitmen yang dapat diandalkan. |
| **Follow-up** | What would your investigation deliver besides more reading? |
| **Weak answer / red flag** | Guarantees a date without checking integration access. |
| **Scoring anchor** | 1 = unsupported certainty · 3 = acknowledges unknowns · 5 = bounded investigation and evidence-based re-estimate |

### Q-SE-09 — Debugging method

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Diagnosis |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | What would you do before changing code for a reported bug? |
| **Pertanyaan (ID)** | Apa yang Anda lakukan sebelum mengubah kode untuk bug yang dilaporkan? |
| **What is assessed** | Reproduction and hypothesis testing. |
| **Evidence basis** | General approach; no specific personal bug is claimed. |
| **Strong answer outline** | Expected/actual; environment; minimal reproduction; evidence; hypothesis. |
| **Model answer (EN)** | I would confirm expected and actual behaviour, input, environment and version. Then I would try a minimal reproduction and trace the relevant boundary, using logs without exposing secrets. I would rank a few hypotheses and test one at a time. If users are seriously affected, I would also escalate and consider safe mitigation. I would not change several unrelated things and call the disappearing symptom a diagnosis. |
| **Contoh jawaban (ID)** | Saya memastikan perilaku yang diharapkan dan aktual, input, lingkungan serta versi. Kemudian saya mencoba reproduksi minimal dan menelusuri batas komponen terkait dengan log yang tidak membocorkan rahasia. Saya mengurutkan beberapa hipotesis lalu mengujinya satu per satu. Jika dampak ke pengguna serius, saya juga mengeskalasi dan mempertimbangkan mitigasi aman. Mengubah banyak hal lalu melihat gejala hilang belum cukup disebut diagnosis. |
| **Follow-up** | What evidence would disprove your first hypothesis? |
| **Weak answer / red flag** | Trial-and-error editing with no reproduction or verification. |
| **Scoring anchor** | 1 = random changes · 3 = reproduces · 5 = falsifiable hypotheses and impact-aware mitigation |

### Q-SE-10 — CI and deployment

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Delivery pipeline |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | Does a green CI pipeline mean a change is safe to release? |
| **Pertanyaan (ID)** | Apakah pipeline CI yang hijau berarti perubahan aman dirilis? |
| **What is assessed** | Scope and limits of automated checks. |
| **Evidence basis** | General knowledge; Iterary automation is documented, exact pipeline unknown. |
| **Strong answer outline** | Only checked conditions; deployment config; migration; acceptance; monitoring. |
| **Model answer (EN)** | A green pipeline means the configured checks passed, not that every risk was checked. I would still consider acceptance criteria, configuration, secrets, migration compatibility and release permissions. After deployment I would verify the intended behaviour and watch relevant signals. My portfolio documents an automated deployment workflow on Iterary, but it does not establish the exact checks or deployment policy, so I would describe those only if I can confirm them. |
| **Contoh jawaban (ID)** | Pipeline hijau berarti pemeriksaan yang dikonfigurasi lolos, bukan seluruh risiko sudah diuji. Saya tetap mempertimbangkan kriteria penerimaan, konfigurasi, rahasia, kompatibilitas migrasi dan izin rilis. Sesudah deployment saya memverifikasi perilaku tujuan dan memantau sinyal terkait. Portofolio saya mencatat alur deployment otomatis pada Iterary, tetapi tidak menjelaskan seluruh pemeriksaan atau kebijakannya; detail itu hanya saya sebut jika dapat dikonfirmasi. |
| **Follow-up** | What post-deployment check would catch a wrong environment variable? |
| **Weak answer / red flag** | Equates build success with user acceptance. |
| **Scoring anchor** | 1 = blind release · 3 = recognises missing checks · 5 = compatibility and observable rollout verification |

### Q-SE-11 — Useful documentation

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Handoff |
| **Difficulty** | Intermediate |
| **Asked in** | Technical / HR |
| **Question (EN)** | What would you document so another developer can maintain a feature? |
| **Pertanyaan (ID)** | Apa yang didokumentasikan agar pengembang lain dapat memelihara fitur? |
| **What is assessed** | Practical knowledge transfer. |
| **Evidence basis** | General approach; Kibang planning/testing documents are documented. |
| **Strong answer outline** | Setup; contracts; decisions; risks; verification/recovery. |
| **Model answer (EN)** | I would document how to run and verify the feature, its API and data contracts, important permissions and the reason for any non-obvious decision. Operational steps and known limitations matter too. I would avoid repeating every line of code in prose. The useful test is whether another person can make a small change or recover from a known failure without relying on my memory. |
| **Contoh jawaban (ID)** | Saya mendokumentasikan cara menjalankan dan memverifikasi fitur, kontrak API serta data, izin penting dan alasan keputusan yang tidak langsung terlihat. Langkah operasional dan keterbatasan juga perlu dicatat. Saya menghindari penjelasan yang sekadar mengulang setiap baris kode. Ukuran kegunaannya adalah apakah orang lain dapat mengubah bagian kecil atau memulihkan kegagalan yang dikenal tanpa bergantung pada ingatan saya. |
| **Follow-up** | Which information belongs in a runbook rather than a code comment? |
| **Weak answer / red flag** | Produces long documents with no setup or recovery instructions. |
| **Scoring anchor** | 1 = no usable handoff · 3 = setup/contracts · 5 = decision context and tested maintenance/recovery steps |

### Q-SE-12 — Technical debt

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Prioritisation |
| **Difficulty** | Intermediate |
| **Asked in** | Technical / business case |
| **Question (EN)** | How would you justify refactoring instead of adding a feature? |
| **Pertanyaan (ID)** | Bagaimana menjelaskan alasan refactor daripada menambah fitur? |
| **What is assessed** | Connecting code quality to delivery risk. |
| **Evidence basis** | Hypothetical reasoning. |
| **Strong answer outline** | Concrete cost/risk; bounded change; tests; compare value. |
| **Model answer (EN)** | I would explain the concrete cost of leaving the structure unchanged, such as repeated defects or slow changes in a critical workflow. Then I would propose a bounded refactor with tests and compare its benefit against the requested feature. Old-looking code alone is not a reason to rewrite. If the risk is modest, I might improve the relevant boundary while delivering the feature rather than request an unrelated overhaul. |
| **Contoh jawaban (ID)** | Saya menjelaskan biaya nyata jika struktur dibiarkan, misalnya bug berulang atau perubahan lambat pada alur penting. Lalu saya mengusulkan refactor terbatas dengan pengujian dan membandingkan manfaatnya dengan fitur yang diminta. Tampilan kode yang tua saja bukan alasan menulis ulang. Bila risikonya kecil, saya dapat memperbaiki batas yang terkait sambil mengerjakan fitur, bukan meminta perombakan besar yang tidak berhubungan. |
| **Follow-up** | What evidence would change your recommendation? |
| **Weak answer / red flag** | Demands a rewrite because a newer framework exists. |
| **Scoring anchor** | 1 = novelty-driven rewrite · 3 = names maintenance cost · 5 = bounded intervention and opportunity cost |

### Q-SE-13 — Incident response

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Operations |
| **Difficulty** | Advanced |
| **Asked in** | Technical / situational |
| **Question (EN)** | A release causes widespread errors. What do you do first? |
| **Pertanyaan (ID)** | Rilis menyebabkan banyak error. Apa tindakan pertama Anda? |
| **What is assessed** | Safe mitigation, communication and evidence. |
| **Evidence basis** | Hypothetical incident; no personal production incident documented. |
| **Strong answer outline** | Assess impact; notify owner; mitigate; preserve evidence; verify; follow-up. |
| **Model answer (EN)** | I would establish impact, inform the responsible team and follow the incident process rather than make uncoordinated changes. If rollback is safe and authorised, it may be the fastest mitigation, but I would check migration compatibility first. I would preserve useful logs, communicate the next checkpoint and verify recovery through user-facing signals. Afterwards I would help investigate the cause and add a regression check without blaming an individual. |
| **Contoh jawaban (ID)** | Saya memastikan dampak, memberi tahu tim yang bertanggung jawab dan mengikuti proses insiden, bukan mengubah sistem tanpa koordinasi. Rollback mungkin mitigasi tercepat jika aman dan diizinkan, tetapi kompatibilitas migrasi harus diperiksa. Saya menjaga bukti log yang relevan, menyampaikan waktu pembaruan berikutnya dan memverifikasi pemulihan lewat sinyal yang dirasakan pengguna. Sesudahnya saya membantu investigasi dan pengujian regresi tanpa menyalahkan individu. |
| **Follow-up** | What if the migration has already changed stored data? |
| **Weak answer / red flag** | Assumes rollback always restores data and changes production alone. |
| **Scoring anchor** | 1 = unsafe improvisation · 3 = mitigation/escalation · 5 = compatibility, evidence and recovery verification |

### Q-SE-14 — Tenant security review

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Security verification |
| **Difficulty** | Advanced |
| **Asked in** | Technical / business case |
| **Question (EN)** | How would you test that a report cannot leak another client's data? |
| **Pertanyaan (ID)** | Bagaimana menguji agar laporan tidak membocorkan data klien lain? |
| **What is assessed** | Authorization across read, cache and export paths. |
| **Evidence basis** | Fictional multi-tenant reporting scenario. |
| **Strong answer outline** | Two tenants; overlapping IDs; scoped queries/cache; exports; revoked membership. |
| **Model answer (EN)** | I would create two tenants with overlapping-looking records and separate memberships, then test direct API access using the other tenant's identifiers. I would include cached results, background exports and download links, not just the visible dashboard. I would also test a revoked membership. The server must derive permitted scope from verified identity and membership; a tenant field sent by the browser is not proof of authorization. |
| **Contoh jawaban (ID)** | Saya membuat dua tenant dengan catatan yang tampak serupa dan keanggotaan terpisah, lalu menguji akses API langsung memakai identifier tenant lain. Hasil cache, ekspor latar belakang dan tautan unduh juga diuji, bukan hanya dashboard. Keanggotaan yang telah dicabut perlu diperiksa pula. Server harus menentukan lingkup dari identitas dan keanggotaan terverifikasi; field tenant yang dikirim browser bukan bukti bahwa pengguna berhak mengaksesnya. |
| **Follow-up** | Why can a correctly filtered API still leak through an export? |
| **Weak answer / red flag** | Tests only whether another client's button is hidden. |
| **Scoring anchor** | 1 = UI-only security · 3 = cross-tenant API test · 5 = cache, job, download and revocation coverage |

### Q-SE-15 — Conflicting review feedback

| Field | Value |
|---|---|
| **Category** | Software engineering |
| **Sub-skill** | Engineering judgement |
| **Difficulty** | Advanced |
| **Asked in** | Technical / behavioural |
| **Question (EN)** | Two reviewers disagree on a design. How would you resolve it? |
| **Pertanyaan (ID)** | Dua peninjau berbeda pendapat tentang desain. Bagaimana Anda menyelesaikannya? |
| **What is assessed** | Decision criteria and constructive collaboration. |
| **Evidence basis** | Hypothetical; no specific candidate review conflict documented. |
| **Strong answer outline** | Restate goals; compare constraints; small experiment; decision owner; record rationale. |
| **Model answer (EN)** | I would restate the requirement and ask which constraint each suggestion addresses. If the disagreement is empirical, such as query performance, I would propose a small representative test. If it is a convention, I would follow the team's decision owner and standards. I would record the chosen reason and revisit condition. I would not treat the discussion as a contest or merge whichever comment arrived last. |
| **Contoh jawaban (ID)** | Saya mengulang kebutuhan dan menanyakan batasan mana yang ditangani setiap usulan. Jika perbedaannya dapat diuji, misalnya performa query, saya mengusulkan percobaan kecil yang representatif. Jika menyangkut konvensi, saya mengikuti standar serta pemilik keputusan tim. Alasan pilihan dan kondisi peninjauan ulang dicatat. Saya tidak menjadikannya persaingan atau memilih komentar terakhir hanya karena paling baru masuk. |
| **Follow-up** | What if the deadline arrives before agreement? |
| **Weak answer / red flag** | Appeals only to seniority or silently ignores one reviewer. |
| **Scoring anchor** | 1 = personal conflict · 3 = discusses criteria · 5 = evidence, ownership and documented trade-off |
