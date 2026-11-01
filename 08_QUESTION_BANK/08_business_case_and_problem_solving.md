# 08 — Business Case and Problem Solving

**Purpose:** Fifteen original bilingual case questions.
**Created / last updated:** 31 October 2026
**Status:** Fictional exercises, not Amber clients, projects or briefs. All answers describe proposed reasoning. Practice scoring is not an employer rubric.
**Schema:** `_SCHEMA.md`

### Q-CASE-01 — Clarify first

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Problem framing |
| **Difficulty** | Foundation |
| **Asked in** | Business case |
| **Question (EN)** | A client asks for a management system. What do you ask first? |
| **Pertanyaan (ID)** | Klien meminta sistem manajemen. Apa yang pertama Anda tanyakan? |
| **What is assessed** | Outcome-led discovery. |
| **Evidence basis** | Fictional generic scenario. |
| **Strong answer outline** | Outcome; users/workflow; first release; constraints; restate. |
| **Model answer (EN)** | I would ask which operational problem the client wants to improve, who performs the workflow and what a successful first release looks like. Then I would clarify existing systems and major constraints. I would not start by choosing a framework. After the answers, I would restate a small scope and separate facts from assumptions so the client can correct my understanding before I design the system. |
| **Contoh jawaban (ID)** | Saya menanyakan masalah operasional yang ingin diperbaiki, siapa yang menjalankan alurnya dan seperti apa rilis awal yang dianggap berhasil. Lalu saya memastikan sistem yang sudah ada serta batasan utama. Saya tidak memulai dari pilihan framework. Setelah mendapat jawaban, saya merangkum lingkup kecil dan memisahkan fakta dari asumsi agar klien dapat mengoreksi pemahaman sebelum desain dibuat. |
| **Follow-up** | Which question would change your architecture choice? |
| **Weak answer / red flag** | Immediately proposes a complete ERP in a favourite stack. |
| **Scoring anchor** | 1 = solution before problem · 3 = relevant questions · 5 = outcome, constraints and confirmed scope |

### Q-CASE-02 — MVP

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Scoping |
| **Difficulty** | Foundation |
| **Asked in** | Business case |
| **Question (EN)** | How would you choose an MVP for school attendance? |
| **Pertanyaan (ID)** | Bagaimana memilih MVP untuk absensi sekolah? |
| **What is assessed** | Small complete workflow and explicit exclusions. |
| **Evidence basis** | Fictional school scenario. |
| **Strong answer outline** | Roster/schedule; capture/correct/report; permissions; defer extras. |
| **Model answer (EN)** | I would choose the smallest workflow that staff can actually use and verify: a valid roster, scheduled sessions, attendance capture, authorised correction and a simple report. Permissions and duplicate prevention belong in that slice, not a later phase. I would defer admissions, fees and advanced analytics unless the client makes them essential. The pilot should demonstrate reliable records, not merely a collection of unfinished screens. |
| **Contoh jawaban (ID)** | Saya memilih alur terkecil yang benar-benar dapat digunakan dan diverifikasi staf: daftar peserta valid, sesi terjadwal, pencatatan absensi, koreksi berizin dan laporan sederhana. Izin akses serta pencegahan duplikasi termasuk dalam alur awal, bukan fase belakangan. Penerimaan siswa, pembayaran dan analitik lanjutan ditunda kecuali menjadi kebutuhan wajib. Pilot harus membuktikan keandalan catatan, bukan sekumpulan layar yang masing-masing belum selesai. |
| **Follow-up** | What acceptance test proves this is an end-to-end slice? |
| **Weak answer / red flag** | Calls every requested feature a must-have. |
| **Scoring anchor** | 1 = unbounded scope · 3 = sensible feature list · 5 = complete workflow, safety and exclusions |

### Q-CASE-03 — Roles

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Authorization |
| **Difficulty** | Foundation |
| **Asked in** | Business case / technical |
| **Question (EN)** | Why is a role name alone insufficient for permission checks? |
| **Pertanyaan (ID)** | Mengapa nama peran saja belum cukup untuk memeriksa izin? |
| **What is assessed** | Object and assignment scope. |
| **Evidence basis** | General design principle; not candidate implementation history. |
| **Strong answer outline** | Role/action/object; assigned class; server check; export scope. |
| **Model answer (EN)** | A role may allow a type of action without granting access to every record. A mentor might correct attendance only for assigned classes. I would check identity, action and the specific object's relationship to that user on the server. The same rule should apply to exports and background jobs. Hiding an admin button improves the interface, but it does not prevent a direct request to an unprotected endpoint. |
| **Contoh jawaban (ID)** | Peran dapat mengizinkan jenis tindakan tanpa memberi akses ke semua catatan. Mentor mungkin hanya boleh mengoreksi absensi kelas yang ditugaskan. Saya memeriksa identitas, tindakan dan hubungan objek tertentu dengan pengguna di server. Aturan yang sama berlaku untuk ekspor dan pekerjaan latar belakang. Menyembunyikan tombol admin membantu antarmuka, tetapi tidak mencegah permintaan langsung ke endpoint yang belum dilindungi. |
| **Follow-up** | What negative test would you write for an assigned mentor? |
| **Weak answer / red flag** | Checks only `role === mentor` for all classes. |
| **Scoring anchor** | 1 = UI/role-only access · 3 = object checks · 5 = consistent checks across API, exports and jobs |

### Q-CASE-04 — Architecture size

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Practicality |
| **Difficulty** | Foundation |
| **Asked in** | Business case |
| **Question (EN)** | Would you start a small internal application with microservices? |
| **Pertanyaan (ID)** | Apakah aplikasi internal kecil sebaiknya langsung memakai microservices? |
| **What is assessed** | Cost-aware architecture. |
| **Evidence basis** | Fictional modest-scale application. |
| **Strong answer outline** | Modular single application; transaction simplicity; operational cost; revisit trigger. |
| **Model answer (EN)** | Not by default. I would usually start with one modular application and a relational database if the team and workload are modest. That simplifies deployment, transactions and diagnosis. Microservices can help when independent scaling or team boundaries justify them, but they add network failures and operational overhead. I would keep clear module boundaries so future separation is possible without paying those costs before there is a demonstrated need. |
| **Contoh jawaban (ID)** | Tidak sebagai pilihan otomatis. Untuk tim dan beban yang sederhana, saya biasanya mulai dari satu aplikasi modular dan basis data relasional. Deployment, transaksi dan diagnosis menjadi lebih sederhana. Microservices berguna bila ada kebutuhan penskalaan mandiri atau batas tim yang jelas, tetapi menambah kegagalan jaringan dan beban operasional. Batas modul tetap dijaga agar pemisahan nanti memungkinkan tanpa membayar kerumitannya sebelum dibutuhkan. |
| **Follow-up** | What concrete evidence would justify extracting one service? |
| **Weak answer / red flag** | Equates more infrastructure with a better design. |
| **Scoring anchor** | 1 = architecture by fashion · 3 = simple justified default · 5 = costs, modularity and revisit condition |

### Q-CASE-05 — Success measure

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Acceptance |
| **Difficulty** | Foundation |
| **Asked in** | Business case |
| **Question (EN)** | How would you know the pilot solved the business problem? |
| **Pertanyaan (ID)** | Bagaimana mengetahui pilot benar-benar menyelesaikan masalah bisnis? |
| **What is assessed** | Outcome validation and baseline discipline. |
| **Evidence basis** | Hypothetical evaluation approach. |
| **Strong answer outline** | Agree measure/baseline; representative pilot; reconcile; user acceptance; no invented target. |
| **Model answer (EN)** | I would agree the success measure and baseline before implementation. For inventory, that might involve reconciling physical counts and traceable stock movements for a representative pilot period. I would also verify that staff can complete the workflow and handle exceptions. The numeric threshold should come from business needs and real observations. A deployed application or attractive dashboard alone does not prove the original problem improved. |
| **Contoh jawaban (ID)** | Saya menyepakati ukuran keberhasilan dan kondisi awal sebelum implementasi. Untuk inventori, contohnya merekonsiliasi hitungan fisik dengan pergerakan stok yang dapat ditelusuri selama periode pilot representatif. Saya juga memverifikasi staf dapat menyelesaikan alur serta menangani pengecualian. Ambang angka harus berasal dari kebutuhan bisnis dan pengamatan nyata. Aplikasi yang sudah dirilis atau dashboard menarik saja belum membuktikan masalah awal membaik. |
| **Follow-up** | What if there is no reliable baseline yet? |
| **Weak answer / red flag** | Invents a 90% improvement target as a fact. |
| **Scoring anchor** | 1 = feature count only · 3 = outcome measure · 5 = agreed baseline, exceptions and acceptance evidence |

### Q-CASE-06 — Assumptions

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Uncertainty |
| **Difficulty** | Foundation |
| **Asked in** | Business case |
| **Question (EN)** | What do you do when a case omits transaction volume? |
| **Pertanyaan (ID)** | Apa yang dilakukan jika kasus tidak menyebut volume transaksi? |
| **What is assessed** | Explicit assumptions without false facts. |
| **Evidence basis** | Hypothetical incomplete brief. |
| **Strong answer outline** | Ask; state bounded assumption; right-size; identify change trigger. |
| **Model answer (EN)** | I would ask for expected daily volume and peak concurrency if questions are allowed. Otherwise I would state a modest-scale assumption explicitly and explain what would change at a larger scale. I would avoid presenting a guessed user count as a fact. The initial design should still protect data integrity; a small workload does not justify unsafe permissions or duplicate-prone writes. I would validate performance with representative data later. |
| **Contoh jawaban (ID)** | Saya menanyakan volume harian dan puncak penggunaan bersamaan jika pertanyaan diperbolehkan. Jika tidak, saya menyatakan asumsi skala sederhana secara jelas dan menjelaskan apa yang berubah pada skala lebih besar. Jumlah pengguna tebakan tidak saya sajikan sebagai fakta. Desain awal tetap harus menjaga integritas; beban kecil bukan alasan untuk izin akses yang lemah atau penulisan rawan duplikasi. Performa divalidasi memakai data representatif kemudian. |
| **Follow-up** | Which part of your design depends most on that assumption? |
| **Weak answer / red flag** | Quietly assumes millions of users or claims exact capacity without tests. |
| **Scoring anchor** | 1 = hidden guess · 3 = labels assumption · 5 = dependency and validation/revisit plan |

### Q-CASE-07 — Build versus buy

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Option comparison |
| **Difficulty** | Intermediate |
| **Asked in** | Business case |
| **Question (EN)** | When would you configure an existing package rather than build? |
| **Pertanyaan (ID)** | Kapan Anda memilih konfigurasi paket yang sudah ada daripada membangun sendiri? |
| **What is assessed** | Total-cost and fit reasoning. |
| **Evidence basis** | General judgement; no candidate ERP implementation evidenced. |
| **Strong answer outline** | Workflow fit; integration/data ownership; licensing; support; gap prototype. |
| **Model answer (EN)** | I would compare workflow fit, integration support, data ownership, licensing and long-term maintenance. If a supported package covers the critical process with limited configuration, it may be safer and faster than custom code. If essential gaps require fragile modifications, I would examine a custom component or another option. I have no documented ERP implementation experience, so I would involve functional and platform specialists rather than promise a fit from a product name. |
| **Contoh jawaban (ID)** | Saya membandingkan kecocokan alur, dukungan integrasi, kepemilikan data, lisensi dan pemeliharaan jangka panjang. Jika paket yang didukung memenuhi proses penting lewat konfigurasi terbatas, pilihan itu bisa lebih aman dan cepat daripada kode khusus. Jika kebutuhan wajib memerlukan modifikasi rapuh, saya mempertimbangkan komponen khusus atau alternatif lain. Saya belum memiliki implementasi ERP terdokumentasi, sehingga perlu melibatkan ahli fungsional dan platform, bukan menjanjikan kecocokan hanya berdasarkan nama produk. |
| **Follow-up** | How would you validate the most important package gap? |
| **Weak answer / red flag** | Says custom is always better or ERP solves everything. |
| **Scoring anchor** | 1 = absolute preference · 3 = compares fit/cost · 5 = supportability, evidence and specialist validation |

### Q-CASE-08 — Retry safety

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Idempotency |
| **Difficulty** | Intermediate |
| **Asked in** | Business case / technical |
| **Question (EN)** | How would you handle duplicate RFID events? |
| **Pertanyaan (ID)** | Bagaimana menangani event RFID yang terkirim berulang? |
| **What is assessed** | Event identity versus business uniqueness. |
| **Evidence basis** | Hypothetical design; SMB integration is documented, implementation details unknown. |
| **Strong answer outline** | Device/event key; atomic dedupe; student/session invariant; acknowledge durable result. |
| **Model answer (EN)** | I would give each device event a stable identifier and enforce uniqueness for the device-event pair. Processing and the relevant attendance change should be coordinated atomically or through a durable job with safe retries. Attendance also needs its own student-session uniqueness rule, because different scans can refer to the same session. This is a proposed approach, not a claim that my documented project implemented exactly these mechanisms. |
| **Contoh jawaban (ID)** | Saya memberi event perangkat identifier stabil dan menegakkan keunikan pasangan perangkat-event. Pemrosesan dan perubahan absensi terkait perlu dikoordinasikan secara atomik atau lewat pekerjaan tahan-gagal yang aman diulang. Absensi tetap membutuhkan aturan unik siswa-sesi, sebab scan berbeda dapat merujuk sesi yang sama. Ini merupakan pendekatan usulan, bukan klaim bahwa proyek saya yang terdokumentasi sudah menerapkan mekanisme persis seperti ini. |
| **Follow-up** | What if two different event IDs represent the same scan session? |
| **Weak answer / red flag** | Deduplicates only in browser memory. |
| **Scoring anchor** | 1 = duplicate-prone · 3 = event key · 5 = durable dedupe plus business invariant |

### Q-CASE-09 — Dashboard freshness

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Data quality |
| **Difficulty** | Intermediate |
| **Asked in** | Business case |
| **Question (EN)** | One report source fails overnight. What should the dashboard show? |
| **Pertanyaan (ID)** | Satu sumber laporan gagal semalam. Apa yang seharusnya tampil di dashboard? |
| **What is assessed** | Honest missing-data presentation. |
| **Evidence basis** | Fictional reporting case. |
| **Strong answer outline** | Freshness/status; last complete snapshot; exceptions; retry/reconcile. |
| **Model answer (EN)** | I would show freshness and source status clearly rather than replace missing figures with zeros. If the report requires a consistent snapshot, I would keep the last complete version and label its age. A partial report could be shown only with an agreed, visible policy. I would record the failed run, notify the responsible owner and retry safely, then reconcile the recovered data before publishing a new complete snapshot. |
| **Contoh jawaban (ID)** | Saya menampilkan kesegaran data dan status sumber secara jelas, bukan mengganti angka hilang dengan nol. Jika laporan membutuhkan snapshot konsisten, saya mempertahankan versi lengkap terakhir dan memberi label usianya. Laporan parsial hanya ditampilkan dengan kebijakan yang disepakati dan terlihat. Run yang gagal dicatat, penanggung jawab diberi tahu, lalu retry dilakukan secara aman dan hasil pemulihan direkonsiliasi sebelum snapshot lengkap baru dipublikasikan. |
| **Follow-up** | How would your answer change for a safety-critical live dashboard? |
| **Weak answer / red flag** | Silently presents stale or partial data as current. |
| **Scoring anchor** | 1 = misleading output · 3 = freshness label · 5 = consistency policy, owner and recovery validation |

### Q-CASE-10 — Critical tests

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Risk-based testing |
| **Difficulty** | Intermediate |
| **Asked in** | Business case / technical |
| **Question (EN)** | With limited time, which tests would you prioritise for a POS? |
| **Pertanyaan (ID)** | Dengan waktu terbatas, pengujian apa yang diprioritaskan untuk POS? |
| **What is assessed** | Prioritising business invariants over superficial coverage. |
| **Evidence basis** | Fictional inventory/POS scenario. |
| **Strong answer outline** | Last-unit race; retries/payment; permissions; positive/negative quantities; reconciliation. |
| **Model answer (EN)** | I would prioritise tests protecting money, stock and access. Two simultaneous buyers for one unit should not both succeed. Repeating an order or payment callback should not duplicate the effect. Invalid quantities and unauthorised warehouse access must be rejected. I would also test a timeout with an unknown payment outcome and verify reconciliation. Visual polish matters, but it would not come before these core integrity checks. |
| **Contoh jawaban (ID)** | Saya memprioritaskan pengujian yang melindungi uang, stok dan akses. Dua pembeli bersamaan untuk satu unit tidak boleh sama-sama berhasil. Pengulangan pesanan atau callback pembayaran tidak boleh menggandakan efek. Kuantitas tidak valid serta akses gudang tanpa izin harus ditolak. Timeout dengan hasil pembayaran belum pasti juga diuji dan direkonsiliasi. Tampilan tetap penting, tetapi tidak mendahului pemeriksaan integritas inti tersebut. |
| **Follow-up** | Which test requires a real database rather than only mocks? |
| **Weak answer / red flag** | Tests only the happy-path checkout screen. |
| **Scoring anchor** | 1 = superficial tests · 3 = important cases · 5 = concurrent/retry/security tests with verification |

### Q-CASE-11 — Personal data

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Privacy |
| **Difficulty** | Intermediate |
| **Asked in** | Business case |
| **Question (EN)** | What extra care does a school system need for children's data? |
| **Pertanyaan (ID)** | Perlindungan tambahan apa yang diperlukan untuk data anak di sistem sekolah? |
| **What is assessed** | Minimisation, scoped access and policy ownership. |
| **Evidence basis** | Fictional school case; not legal advice. |
| **Strong answer outline** | Minimise; verify guardian; restrict exports/logs; retention; responsible legal owner. |
| **Model answer (EN)** | I would minimise collected data and verify who may access each child's records, including guardian relationships. Exports, logs and backups need protection too, not only the main screen. I would use synthetic data during development and agree retention, correction and deletion procedures with the responsible school and legal staff. I would not invent a universal consent or retention rule from memory, because the applicable obligations need authoritative confirmation. |
| **Contoh jawaban (ID)** | Saya membatasi data yang dikumpulkan dan memverifikasi siapa yang berhak melihat catatan setiap anak, termasuk hubungan wali. Ekspor, log dan backup juga perlu dilindungi, bukan hanya layar utama. Pengembangan memakai data sintetis; retensi, koreksi dan penghapusan disepakati bersama pihak sekolah serta hukum yang bertanggung jawab. Saya tidak mengarang aturan persetujuan atau retensi universal dari ingatan, karena kewajiban yang berlaku perlu dikonfirmasi secara otoritatif. |
| **Follow-up** | How would you test that one guardian cannot access another child's export? |
| **Weak answer / red flag** | Assumes an admin login or soft-delete flag solves all privacy obligations. |
| **Scoring anchor** | 1 = ignores sensitive data · 3 = access controls · 5 = lifecycle, secondary copies and policy ownership |

### Q-CASE-12 — Delivery plan

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Sequencing |
| **Difficulty** | Intermediate |
| **Asked in** | Business case |
| **Question (EN)** | How would you sequence a legacy ERP integration pilot? |
| **Pertanyaan (ID)** | Bagaimana mengurutkan pilot integrasi ERP lama? |
| **What is assessed** | Dependencies and safe rollout. |
| **Evidence basis** | Fictional integration case; no candidate ERP experience claimed. |
| **Strong answer outline** | Ownership/contract; sandbox; read-only; reconciliation; limited writes; rollback limits. |
| **Model answer (EN)** | I would first confirm data ownership and supported interfaces, then obtain a safe test environment and validate mappings. I would start with read-only status and reconciliation before allowing a limited order-submission pilot. Duplicate handling, timeout recovery and support ownership should be tested before expansion. I would not write directly into vendor tables without support, or promise that rolling back the portal reverses orders already accepted by the ERP. |
| **Contoh jawaban (ID)** | Saya memastikan kepemilikan data dan interface yang didukung, lalu mendapatkan lingkungan uji aman serta memvalidasi mapping. Saya memulai dari status read-only dan rekonsiliasi sebelum pilot terbatas untuk pengiriman pesanan. Duplikasi, pemulihan timeout dan pemilik dukungan diuji sebelum perluasan. Saya tidak menulis langsung ke tabel vendor tanpa dukungan, atau menjanjikan rollback portal akan membatalkan pesanan yang sudah diterima ERP. |
| **Follow-up** | What dependency could block the pilot before any coding? |
| **Weak answer / red flag** | Begins with production writes and no reconciliation. |
| **Scoring anchor** | 1 = unsafe rollout · 3 = staged plan · 5 = supported contract, dependencies and failure acceptance |

### Q-CASE-13 — Offline stock

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Distributed consistency |
| **Difficulty** | Advanced |
| **Asked in** | Business case / technical |
| **Question (EN)** | Can unrestricted offline POS sales guarantee no overselling of shared stock? |
| **Pertanyaan (ID)** | Bisakah penjualan POS offline tanpa batas menjamin stok bersama tidak terjual berlebih? |
| **What is assessed** | Recognising an unavoidable trade-off. |
| **Evidence basis** | Fictional inventory scenario. |
| **Strong answer outline** | No fresh global coordination; quotas/online/provisional; business approval; reconciliation. |
| **Model answer (EN)** | Not without additional constraints. An offline counter cannot know what another counter has just sold from the same stock pool. I would offer online confirmation, dedicated offline quotas or explicitly provisional sales with later reconciliation. Each changes the customer experience or operational process. I would ask the business to choose the acceptable risk rather than claim that caching or eventual synchronisation alone guarantees inventory consistency. |
| **Contoh jawaban (ID)** | Tidak tanpa batasan tambahan. Kasir offline tidak mengetahui penjualan terbaru kasir lain dari persediaan yang sama. Saya menawarkan konfirmasi online, kuota khusus offline atau penjualan provisional yang direkonsiliasi kemudian. Masing-masing mengubah pengalaman pelanggan atau proses operasional. Saya meminta bisnis memilih risiko yang dapat diterima, bukan mengklaim cache atau sinkronisasi belakangan saja sudah menjamin konsistensi persediaan bersama. |
| **Follow-up** | How would you allocate and reclaim an offline quota? |
| **Weak answer / red flag** | Promises global consistency while every counter sells unrestricted offline. |
| **Scoring anchor** | 1 = impossible guarantee · 3 = recognises trade-off · 5 = explicit alternatives and business consequence |

### Q-CASE-14 — ERP timeout

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Failure semantics |
| **Difficulty** | Advanced |
| **Asked in** | Business case / technical |
| **Question (EN)** | An ERP order request times out after submission. Do you create it again? |
| **Pertanyaan (ID)** | Permintaan pesanan ERP timeout setelah dikirim. Apakah Anda membuatnya lagi? |
| **What is assessed** | Unknown outcomes, identity and safe retry. |
| **Evidence basis** | Fictional integration scenario. |
| **Strong answer outline** | Timeout ambiguous; external ID lookup; same key; uncertainty queue if unsupported. |
| **Model answer (EN)** | I would treat the outcome as unknown, because the ERP may have accepted the order before the response was lost. I would look up the stable external request ID or retry through a supported idempotent mechanism using the same key. If the ERP cannot identify duplicates safely, I would place the request in an exception workflow for reconciliation rather than automatically create another order. The portal should show pending, not a false success or failure. |
| **Contoh jawaban (ID)** | Saya memperlakukan hasilnya sebagai belum diketahui, karena ERP mungkin menerima pesanan sebelum respons hilang. Saya mencari ID permintaan eksternal yang stabil atau memakai mekanisme idempoten yang didukung dengan kunci sama. Jika ERP tidak mampu mengenali duplikasi secara aman, permintaan masuk alur pengecualian untuk rekonsiliasi, bukan otomatis dibuat ulang. Portal menampilkan status pending, bukan keberhasilan atau kegagalan yang belum terbukti. |
| **Follow-up** | What information should an operator see in that exception queue? |
| **Weak answer / red flag** | Repeats creation with a new ID until a response arrives. |
| **Scoring anchor** | 1 = duplicate creation · 3 = stable retry key · 5 = supported lookup, visible uncertainty and reconciliation |

### Q-CASE-15 — Defend then revise

| Field | Value |
|---|---|
| **Category** | Business case and problem solving |
| **Sub-skill** | Trade-off reasoning |
| **Difficulty** | Advanced |
| **Asked in** | Business case |
| **Question (EN)** | What would make you change a daily-batch reporting recommendation? |
| **Pertanyaan (ID)** | Kondisi apa yang membuat Anda mengubah rekomendasi laporan batch harian? |
| **What is assessed** | Evidence-based revisit criteria. |
| **Evidence basis** | Fictional reporting design. |
| **Strong answer outline** | Decision latency; source capability; total cost; incremental alternative; quality/reconciliation. |
| **Model answer (EN)** | I would revisit daily batch if an important business decision requires fresher data and the sources can support reliable incremental updates. I would first compare more frequent batches with event-driven processing, rather than jump straight to a complex stream platform. Lower latency adds operating and reconciliation costs, and it does not fix unclear metric definitions. I would agree the freshness requirement and test the smallest change that satisfies it. |
| **Contoh jawaban (ID)** | Saya meninjau batch harian jika keputusan bisnis penting memerlukan data lebih segar dan sumber mendukung pembaruan inkremental yang andal. Saya membandingkan batch lebih sering dengan pemrosesan berbasis event terlebih dahulu, bukan langsung memilih platform streaming rumit. Latensi rendah menambah biaya operasi dan rekonsiliasi, serta tidak memperbaiki definisi metrik yang kabur. Kebutuhan kesegaran disepakati, lalu perubahan terkecil yang memenuhinya diuji. |
| **Follow-up** | Which quality checks remain necessary with streaming? |
| **Weak answer / red flag** | Treats real-time as automatically better and always required. |
| **Scoring anchor** | 1 = fashion-driven change · 3 = names freshness trigger · 5 = alternatives, source limits and quality costs |
