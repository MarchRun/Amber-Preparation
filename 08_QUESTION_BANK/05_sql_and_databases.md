# 05 — SQL and Databases

**Purpose:** Fifteen original bilingual oral/whiteboard questions.
**Created / last updated:** 31 October 2026
**Status:** General-knowledge model answers; "I would" describes proposed reasoning, not past candidate implementation. Practice anchors are not Amber's rubric.
**Schema:** `_SCHEMA.md`. Query exercises: `../05_TECHNICAL_PREPARATION/sql_and_databases.md`.

### Q-SQL-01 — Join choice

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | Join semantics |
| **Difficulty** | Foundation |
| **Asked in** | Technical / business case |
| **Question (EN)** | How would you list every department, including departments with no employees? |
| **Pertanyaan (ID)** | Bagaimana menampilkan semua departemen, termasuk yang tidak memiliki pegawai? |
| **What is assessed** | Preserving unmatched rows and counting correctly. |
| **Evidence basis** | General knowledge; no claim about a past query. |
| **Strong answer outline** | Start from departments; LEFT JOIN employees; count employee ID; group by department. |
| **Model answer (EN)** | I would start from departments and left join employees on the department key. That keeps a department even when no employee matches. For headcount I would count the employee ID, not count every joined row, because the unmatched department still produces a null-extended row. I would group by the department identifier and name, and test one department with zero employees. |
| **Contoh jawaban (ID)** | Saya akan mulai dari departemen lalu memakai LEFT JOIN ke pegawai berdasarkan kunci departemen. Departemen tetap muncul ketika tidak ada pegawai yang cocok. Untuk jumlah pegawai saya menghitung ID pegawai, bukan seluruh baris hasil join, karena departemen tanpa pasangan tetap menghasilkan satu baris dengan nilai null. Saya mengelompokkan berdasarkan ID dan nama departemen, lalu menguji departemen yang benar-benar belum memiliki pegawai. |
| **Follow-up** | What changes if you put an employee-status filter in WHERE? |
| **Weak answer / red flag** | Uses INNER JOIN or COUNT(*) and reports one employee for an empty department. |
| **Scoring anchor** | 1 = wrong join/count · 3 = correct join · 5 = explains null row and filter placement |

### Q-SQL-02 — WHERE and HAVING

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | Aggregation |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | What is the difference between WHERE and HAVING? |
| **Pertanyaan (ID)** | Apa perbedaan WHERE dan HAVING? |
| **What is assessed** | Row filtering versus group filtering. |
| **Evidence basis** | General knowledge. |
| **Strong answer outline** | WHERE before grouping; HAVING after grouping; aggregate example. |
| **Model answer (EN)** | WHERE selects input rows before grouping, while HAVING filters the resulting groups. To find departments with more than five active employees, I would put the active condition in WHERE, group by department, then put the count condition in HAVING. That also makes the intended denominator clear. I would not move filters between the two clauses without checking whether the meaning changes. |
| **Contoh jawaban (ID)** | WHERE memilih baris sebelum pengelompokan, sedangkan HAVING menyaring kelompok yang dihasilkan. Untuk mencari departemen dengan lebih dari lima pegawai aktif, saya menaruh syarat aktif di WHERE, mengelompokkan berdasarkan departemen, lalu menaruh syarat jumlah di HAVING. Dengan begitu, yang dihitung memang hanya pegawai aktif. Saya tidak akan memindahkan kondisi antarbagian tanpa memeriksa apakah arti hasilnya berubah. |
| **Follow-up** | Can HAVING be used without an explicit GROUP BY? |
| **Weak answer / red flag** | Says the clauses are interchangeable or puts COUNT(*) in ordinary WHERE. |
| **Scoring anchor** | 1 = confuses clauses · 3 = correct distinction · 5 = correct example and changed-population reasoning |

### Q-SQL-03 — Keys

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | Integrity |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | Why use both a primary key and a foreign key? |
| **Pertanyaan (ID)** | Mengapa tabel membutuhkan primary key dan foreign key? |
| **What is assessed** | Identity versus referential integrity. |
| **Evidence basis** | General knowledge. |
| **Strong answer outline** | Row identity; valid reference; separate business uniqueness; nullable references. |
| **Model answer (EN)** | A primary key identifies a row uniquely and cannot be null. A foreign key requires a referenced value to exist in the parent key, unless the relationship permits null. They protect different things. For attendance I would identify the record and reference valid students and sessions. I would also enforce uniqueness of the student-session pair, because a surrogate ID alone does not prevent duplicate attendance. |
| **Contoh jawaban (ID)** | Primary key mengidentifikasi baris secara unik dan tidak boleh null. Foreign key memastikan nilai rujukan tersedia di tabel induk, kecuali hubungan memang mengizinkan null. Keduanya melindungi hal yang berbeda. Untuk absensi saya membutuhkan identitas catatan serta rujukan ke siswa dan sesi yang valid. Saya juga memberi batasan unik pada pasangan siswa-sesi, karena ID pengganti saja tidak mencegah absensi ganda untuk pasangan yang sama. |
| **Follow-up** | Does PostgreSQL automatically index every referencing foreign-key column? |
| **Weak answer / red flag** | Assumes any primary key prevents all business duplicates. |
| **Scoring anchor** | 1 = incorrect purpose · 3 = distinguishes keys · 5 = adds business uniqueness and null policy |

### Q-SQL-04 — Normalisation

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | Modelling |
| **Difficulty** | Foundation |
| **Asked in** | Technical / business case |
| **Question (EN)** | What problem does normalisation solve? |
| **Pertanyaan (ID)** | Masalah apa yang diselesaikan normalisasi basis data? |
| **What is assessed** | Dependency reasoning rather than memorised labels. |
| **Evidence basis** | General knowledge. |
| **Strong answer outline** | Repeated facts; update anomalies; separate entities; deliberate denormalisation. |
| **Model answer (EN)** | Normalisation organises facts according to their dependencies so updates do not leave inconsistent copies. If every employee row repeats the department name, renaming a department can miss some rows. I would keep the department fact in its own table and reference it. I would explain first, second and third normal forms using keys and dependencies, then consider denormalisation only for a measured access need. |
| **Contoh jawaban (ID)** | Normalisasi menempatkan fakta sesuai ketergantungannya agar perubahan tidak meninggalkan salinan yang saling bertentangan. Jika nama departemen diulang pada setiap pegawai, pergantian nama dapat terlewat di sebagian baris. Saya akan menyimpan fakta departemen di tabel sendiri dan merujuknya. Setelah menjelaskan bentuk normal lewat kunci dan ketergantungan, saya baru mempertimbangkan denormalisasi untuk kebutuhan akses yang benar-benar terukur, bukan karena menganggap join selalu lambat. |
| **Follow-up** | What is a partial dependency on a composite key? |
| **Weak answer / red flag** | Says normalisation only means splitting a large table. |
| **Scoring anchor** | 1 = arbitrary splitting · 3 = explains duplication · 5 = dependency/anomaly example and trade-off |

### Q-SQL-05 — Null values

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | Null semantics |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | Why does `column = NULL` not find missing values? |
| **Pertanyaan (ID)** | Mengapa `column = NULL` tidak menemukan nilai yang kosong? |
| **What is assessed** | Three-valued logic and missing-data care. |
| **Evidence basis** | General knowledge. |
| **Strong answer outline** | Unknown comparison; IS NULL; COUNT differences; avoid silent zero. |
| **Model answer (EN)** | NULL represents a missing or unknown value, so ordinary equality with it does not evaluate to true. I would use IS NULL or IS NOT NULL. I would also distinguish COUNT(*) from COUNT(column), because the latter excludes null values. For reports I would not automatically convert missing data to zero; that can change the business meaning and hide an incomplete source. |
| **Contoh jawaban (ID)** | NULL menyatakan nilai yang belum diketahui atau tidak tersedia, sehingga perbandingan kesetaraan biasa tidak menghasilkan true. Saya memakai IS NULL atau IS NOT NULL. Saya juga membedakan COUNT(*) dan COUNT(column), karena yang kedua mengabaikan null. Dalam laporan, saya tidak otomatis mengganti data yang hilang dengan nol; tindakan itu bisa mengubah makna bisnis dan menutupi sumber data yang belum lengkap. |
| **Follow-up** | What happens with NOT IN when its subquery returns a NULL? |
| **Weak answer / red flag** | Treats null, empty string and numeric zero as equivalent. |
| **Scoring anchor** | 1 = uses = NULL · 3 = uses IS NULL · 5 = explains unknown and reporting consequences |

### Q-SQL-06 — Injection prevention

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | Query security |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | How would you prevent SQL injection? |
| **Pertanyaan (ID)** | Bagaimana Anda mencegah SQL injection? |
| **What is assessed** | Separation of query structure from input. |
| **Evidence basis** | General knowledge; no claim about candidate security implementation. |
| **Strong answer outline** | Parameters; allowlisted identifiers; least privilege; validation still needed. |
| **Model answer (EN)** | I would use parameterised queries or correctly configured query-builder bindings, rather than concatenate user input into SQL. Parameters represent values, not arbitrary table names or sort directions, so dynamic identifiers need an allowlist. I would validate business input and restrict database privileges as well. Escaping alone is easy to misuse, and a safe SQL statement can still expose another user's data if authorization is missing. |
| **Contoh jawaban (ID)** | Saya memakai query berparameter atau binding query builder yang benar, bukan menggabungkan input pengguna ke teks SQL. Parameter mewakili nilai, bukan nama tabel atau arah pengurutan secara bebas, sehingga identifier dinamis perlu allowlist. Validasi bisnis dan hak akses basis data minimum tetap diperlukan. Escaping mudah disalahgunakan, dan query yang aman dari injection masih bisa membocorkan data orang lain jika pemeriksaan izin tidak dilakukan. |
| **Follow-up** | How would you safely let users choose a sort column? |
| **Weak answer / red flag** | Relies only on removing quote characters. |
| **Scoring anchor** | 1 = string concatenation · 3 = parameters · 5 = identifier allowlist and separate authorization |

### Q-SQL-07 — Index cost

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | Performance |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | Why not create an index on every column? |
| **Pertanyaan (ID)** | Mengapa tidak membuat indeks pada setiap kolom? |
| **What is assessed** | Read/write trade-offs and measurement. |
| **Evidence basis** | General knowledge. |
| **Strong answer outline** | Read benefit; write/storage cost; access pattern; query plan. |
| **Model answer (EN)** | Indexes can reduce search and sorting work, but each one consumes storage and must be maintained during writes. I would choose them from actual filters, joins and ordering, then inspect the query plan with representative data. A sequential scan may be better for a small table or a query returning most rows. Composite index order matters, so indexing every column independently is not a substitute for understanding the workload. |
| **Contoh jawaban (ID)** | Indeks dapat mengurangi pekerjaan pencarian dan pengurutan, tetapi memerlukan ruang dan pemeliharaan setiap kali data ditulis. Saya memilihnya berdasarkan filter, join, dan urutan hasil yang nyata, lalu memeriksa rencana query dengan data representatif. Sequential scan bisa lebih tepat untuk tabel kecil atau query yang membaca sebagian besar baris. Urutan indeks gabungan juga penting; memberi indeks terpisah pada semua kolom bukan pengganti pemahaman pola akses. |
| **Follow-up** | Would an index on `(student_id, session_id)` help a session-only report? |
| **Weak answer / red flag** | Claims indexes always make all operations faster. |
| **Scoring anchor** | 1 = universal speed claim · 3 = mentions write cost · 5 = workload, plan and composite-order reasoning |

### Q-SQL-08 — Transaction boundary

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | ACID |
| **Difficulty** | Intermediate |
| **Asked in** | Technical / business case |
| **Question (EN)** | Which changes should be in one order transaction? |
| **Pertanyaan (ID)** | Perubahan apa yang harus berada dalam satu transaksi pemesanan? |
| **What is assessed** | Atomic business updates and external boundaries. |
| **Evidence basis** | Hypothetical inventory scenario. |
| **Strong answer outline** | Order/lines/stock together; rollback; short locks; external payment separate. |
| **Model answer (EN)** | I would keep the order, its lines, stock reservation and matching history consistent in one short database transaction. If a required change fails, the transaction should roll back. I would not hold database locks while waiting for an external payment provider. Instead, I would model payment as a separate stateful workflow with stable identifiers and reconciliation. Atomicity within one database does not make a remote payment atomic with it. |
| **Contoh jawaban (ID)** | Saya akan menjaga pesanan, rincian, reservasi stok dan riwayat terkait dalam satu transaksi basis data yang singkat. Jika perubahan wajib gagal, transaksi dibatalkan. Saya tidak menahan kunci basis data sambil menunggu penyedia pembayaran eksternal. Pembayaran saya modelkan sebagai alur status tersendiri dengan identifier stabil dan rekonsiliasi. Sifat atomik dalam satu basis data tidak otomatis menjadikan pembayaran pada sistem lain ikut atomik dengan transaksi tersebut. |
| **Follow-up** | What if payment succeeds but the response times out? |
| **Weak answer / red flag** | Says BEGIN/COMMIT makes external services exactly-once. |
| **Scoring anchor** | 1 = unsafe boundary · 3 = groups local writes · 5 = explains remote uncertainty and reconciliation |

### Q-SQL-09 — Salary ranking

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | Window functions |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | How do ROW_NUMBER, RANK and DENSE_RANK differ with ties? |
| **Pertanyaan (ID)** | Bagaimana ROW_NUMBER, RANK dan DENSE_RANK menangani nilai yang sama? |
| **What is assessed** | Tie semantics and deterministic ordering. |
| **Evidence basis** | General knowledge. |
| **Strong answer outline** | Unique sequence; gaps; no gaps; specify top rows versus salary levels. |
| **Model answer (EN)** | ROW_NUMBER assigns a different position to each row, so I need a unique tiebreaker for deterministic results. RANK gives equal values the same position and leaves gaps afterwards. DENSE_RANK gives equal values the same position without gaps. I would first clarify whether top two means two employees or two distinct salary levels. That requirement determines the function, not just which syntax I remember. |
| **Contoh jawaban (ID)** | ROW_NUMBER memberi nomor berbeda untuk setiap baris, sehingga saya memerlukan pembeda unik agar hasilnya deterministik. RANK memberi peringkat sama untuk nilai yang sama dan menyisakan lompatan setelahnya. DENSE_RANK tidak menyisakan lompatan tersebut. Saya akan memastikan apakah dua teratas berarti dua pegawai atau dua tingkat gaji berbeda. Kebutuhan itu yang menentukan fungsi, bukan sekadar sintaks yang paling saya ingat. |
| **Follow-up** | For salaries 100, 100, 90, what does each function return? |
| **Weak answer / red flag** | Treats all three functions as synonyms. |
| **Scoring anchor** | 1 = wrong tie behaviour · 3 = correct definitions · 5 = maps business requirement to deterministic query |

### Q-SQL-10 — Join multiplication

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | Aggregation correctness |
| **Difficulty** | Intermediate |
| **Asked in** | Technical / business case |
| **Question (EN)** | Why does joining employees and projects inflate a department budget total? |
| **Pertanyaan (ID)** | Mengapa join pegawai dan proyek dapat membuat total anggaran departemen membesar? |
| **What is assessed** | Join cardinality and independent aggregation. |
| **Evidence basis** | General knowledge. |
| **Strong answer outline** | Multiple one-to-many paths; Cartesian multiplication within department; aggregate separately. |
| **Model answer (EN)** | If one department has several employees and several projects, joining both detail tables produces combinations of employee and project rows. Each project budget is repeated for every matching employee. I would aggregate headcount and budget separately by department, then join those summaries. SUM DISTINCT is not a general fix because two legitimate projects can have the same budget. I would verify a small example by hand. |
| **Contoh jawaban (ID)** | Jika satu departemen mempunyai beberapa pegawai dan proyek, join kedua tabel detail menghasilkan kombinasi baris pegawai-proyek. Anggaran setiap proyek terulang untuk setiap pegawai yang cocok. Saya akan menghitung jumlah pegawai dan total anggaran secara terpisah per departemen, kemudian menggabungkan ringkasannya. SUM DISTINCT bukan solusi umum, karena dua proyek sah bisa memiliki anggaran sama. Saya akan memverifikasi contoh kecil secara manual terlebih dahulu. |
| **Follow-up** | Show the row count for two employees and three projects. |
| **Weak answer / red flag** | Adds DISTINCT until the result looks plausible. |
| **Scoring anchor** | 1 = misses multiplication · 3 = identifies duplicates · 5 = preaggregation and equal-budget counterexample |

### Q-SQL-11 — Pagination

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | Stable reads |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | When would you use keyset pagination rather than OFFSET? |
| **Pertanyaan (ID)** | Kapan Anda memilih keyset pagination daripada OFFSET? |
| **What is assessed** | Performance and stable ordering. |
| **Evidence basis** | General knowledge. |
| **Strong answer outline** | Deep offset cost; stable cursor; unique tiebreaker; page-jump trade-off. |
| **Model answer (EN)** | OFFSET is simple for small lists and direct page numbers, but deep offsets may require scanning many skipped rows and concurrent changes can shift results. Keyset pagination continues after the last ordering key, such as timestamp and ID together. I would use a matching index and a unique tiebreaker. The trade-off is that jumping to an arbitrary page is less natural, and cursor semantics need a clear contract. |
| **Contoh jawaban (ID)** | OFFSET sederhana untuk daftar kecil dan nomor halaman langsung, tetapi offset besar bisa membaca banyak baris yang kemudian dilewati. Perubahan bersamaan juga dapat menggeser hasil. Keyset melanjutkan setelah kunci urutan terakhir, misalnya timestamp bersama ID. Saya memakai indeks yang sesuai dan pembeda unik. Kekurangannya, lompat ke sembarang nomor halaman tidak lagi sederhana dan arti cursor harus dijelaskan dalam kontrak API. |
| **Follow-up** | What happens if two records share the same timestamp? |
| **Weak answer / red flag** | Uses an unstable sort or cursor without a tiebreaker. |
| **Scoring anchor** | 1 = unstable query · 3 = correct cursor idea · 5 = index, tiebreaker and navigation trade-off |

### Q-SQL-12 — Soft deletion

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | Lifecycle |
| **Difficulty** | Intermediate |
| **Asked in** | Technical / business case |
| **Question (EN)** | What complications does soft deletion introduce? |
| **Pertanyaan (ID)** | Kerumitan apa yang muncul ketika memakai soft delete? |
| **What is assessed** | Retention, uniqueness and reporting. |
| **Evidence basis** | General knowledge. |
| **Strong answer outline** | Default filters; unique constraints; audit/retention; not legal erasure. |
| **Model answer (EN)** | Marking a row deleted preserves history, but every relevant query must apply the right visibility rule. Unique constraints may still block reuse of an identifier, and reports must distinguish inactive records from historical facts. I would define restore behaviour and references before choosing soft deletion. It is not the same as erasing personal data, so retention and legal obligations need an explicit policy rather than a deleted flag alone. |
| **Contoh jawaban (ID)** | Menandai baris sebagai terhapus mempertahankan riwayat, tetapi setiap query terkait perlu menerapkan aturan visibilitas yang benar. Batasan unik mungkin tetap menghalangi pemakaian ulang identifier, dan laporan harus membedakan catatan nonaktif dari fakta historis. Saya akan menentukan perilaku pemulihan serta referensinya sebelum memilih soft delete. Ini bukan penghapusan data pribadi secara nyata; retensi dan kewajiban hukum membutuhkan kebijakan, bukan hanya sebuah flag. |
| **Follow-up** | How would you handle a unique email among active accounts only? |
| **Weak answer / red flag** | Says soft delete satisfies every deletion or privacy requirement. |
| **Scoring anchor** | 1 = ignores lifecycle · 3 = notes filters · 5 = uniqueness, restore and retention policy |

### Q-SQL-13 — Last-item race

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | Concurrency |
| **Difficulty** | Advanced |
| **Asked in** | Technical / business case |
| **Question (EN)** | Two buyers request the final unit. How do you prevent overselling? |
| **Pertanyaan (ID)** | Dua pembeli meminta unit terakhir. Bagaimana mencegah stok terjual ganda? |
| **What is assessed** | Atomic invariant enforcement. |
| **Evidence basis** | Hypothetical inventory scenario. |
| **Strong answer outline** | Unsafe read/write; conditional update or lock; transaction; conflict test. |
| **Model answer (EN)** | I would not read quantity and later write a calculated value without protection. One approach is a conditional update that decrements only when available stock is sufficient, then checks the affected-row count. The order and ledger changes belong in the same transaction. Another approach locks the stock row before checking. I would test two simultaneous requests and expect one success, one clear rejection, and no inconsistent stock history. |
| **Contoh jawaban (ID)** | Saya tidak membaca jumlah stok lalu menulis hasil pengurangan belakangan tanpa perlindungan. Salah satu cara adalah update bersyarat yang hanya mengurangi ketika stok tersedia mencukupi, kemudian memeriksa jumlah baris terdampak. Perubahan pesanan dan ledger berada dalam transaksi yang sama. Alternatifnya mengunci baris stok sebelum memeriksa. Saya akan menguji dua permintaan bersamaan: satu berhasil, satu ditolak dengan jelas, dan riwayat stok tetap konsisten. |
| **Follow-up** | What if the order contains several products? |
| **Weak answer / red flag** | Assumes any transaction automatically prevents every race. |
| **Scoring anchor** | 1 = unprotected read/write · 3 = lock or guarded update · 5 = atomic ledger/order and concurrent test |

### Q-SQL-14 — Migration safety

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | Production change |
| **Difficulty** | Advanced |
| **Asked in** | Technical |
| **Question (EN)** | How would you add a required field to a large live table safely? |
| **Pertanyaan (ID)** | Bagaimana menambah kolom wajib pada tabel besar yang sedang dipakai? |
| **What is assessed** | Compatibility, backfill and locking awareness. |
| **Evidence basis** | Proposed approach; no candidate production migration is documented. |
| **Strong answer outline** | Check engine/locks; additive schema; compatible app; backfill; enforce constraint later. |
| **Model answer (EN)** | I would check the database version, lock behaviour, data volume and deployment compatibility first. A common sequence is to add a nullable field, deploy code that can handle both states, backfill in controlled batches, validate completeness, then enforce the required constraint. Exact steps depend on the engine and column definition. I would monitor impact and plan recovery; rolling back code does not automatically reverse a destructive data change. |
| **Contoh jawaban (ID)** | Saya memeriksa versi basis data, perilaku locking, volume dan kompatibilitas deployment terlebih dahulu. Urutan yang sering sesuai adalah menambah kolom nullable, merilis kode yang menangani kedua keadaan, melakukan backfill bertahap, memvalidasi kelengkapan, lalu menegakkan batasan wajib. Langkah tepatnya bergantung pada engine dan definisi kolom. Dampaknya harus dipantau serta pemulihannya direncanakan; rollback kode tidak otomatis membalik perubahan data yang merusak. |
| **Follow-up** | What would make you stop or postpone the migration? |
| **Weak answer / red flag** | Runs an untested blocking alteration and promises easy rollback. |
| **Scoring anchor** | 1 = unsafe live change · 3 = staged migration · 5 = engine-specific verification, compatibility and recovery |

### Q-SQL-15 — Attendance denominator

| Field | Value |
|---|---|
| **Category** | SQL and databases |
| **Sub-skill** | Business semantics |
| **Difficulty** | Advanced |
| **Asked in** | Business case / technical |
| **Question (EN)** | Why can attendance percentage calculated from attendance rows be misleading? |
| **Pertanyaan (ID)** | Mengapa persentase yang dihitung hanya dari baris absensi bisa menyesatkan? |
| **What is assessed** | Correct population and missing-data interpretation. |
| **Evidence basis** | General knowledge; not a claim about SMB's actual reporting. |
| **Strong answer outline** | Recorded versus scheduled population; enrollment dates; cancellation/leave; missing status. |
| **Model answer (EN)** | If I divide present rows by recorded rows, a student with missing records may appear fully present. The business denominator is usually eligible scheduled sessions, with explicit rules for enrollment dates, cancellation and leave. I would start from the schedule and eligible enrollment, then join attendance. Missing, absent and excused are different states. I would confirm the policy before publishing the percentage and show the denominator for reconciliation. |
| **Contoh jawaban (ID)** | Jika jumlah hadir dibagi jumlah baris tercatat, siswa yang datanya belum lengkap dapat tampak selalu hadir. Penyebut bisnis biasanya sesi terjadwal yang memang wajib diikuti, dengan aturan tanggal pendaftaran, pembatalan dan izin. Saya mulai dari jadwal serta peserta yang memenuhi syarat, kemudian menggabungkan absensi. Belum tercatat, tidak hadir dan izin adalah keadaan berbeda. Kebijakannya perlu dikonfirmasi dan penyebut ditampilkan agar dapat direkonsiliasi. |
| **Follow-up** | How would you represent a student who joined halfway through the term? |
| **Weak answer / red flag** | Treats every missing row as present or silently excludes it. |
| **Scoring anchor** | 1 = wrong denominator · 3 = mentions schedule · 5 = eligibility, policy and missing-data tests |
