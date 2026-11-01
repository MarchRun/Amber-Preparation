# Technical Glossary — 100 Terms

**Purpose:** Explain technical ideas in English and understand them in Indonesian.
**Created / last updated:** 31 October 2026
**Use:** Cover the meaning; explain the example aloud. General knowledge, not candidate skill certification.

| # | Term | Arti singkat (ID) | Example / use |
|---:|---|---|---|
| 1 | Variable | Nama yang merujuk nilai | `count = 3` |
| 2 | Type | Himpunan nilai dan operasi yang valid | A string is not a number |
| 3 | Primitive | Nilai dasar, bukan objek biasa | Boolean flag |
| 4 | Reference | Nilai yang menunjuk objek | Two bindings share an object |
| 5 | Mutation | Mengubah isi nilai/objek | Append to an array |
| 6 | Immutability | Nilai tidak diubah setelah dibuat | Return a new state object |
| 7 | Scope | Wilayah berlakunya nama | Block-local variable |
| 8 | Closure | Fungsi yang mempertahankan lingkungan leksikal | Callback remembers configuration |
| 9 | Recursion | Fungsi memanggil dirinya | Traverse a tree |
| 10 | Base case | Kondisi berhenti rekursi | Empty subtree |
| 11 | Encapsulation | Membatasi perubahan keadaan lewat kontrak | Validate stock changes |
| 12 | Abstraction | Menyembunyikan detail yang tidak perlu | Payment gateway interface |
| 13 | Inheritance | Spesialisasi tipe induk | Extend a base class |
| 14 | Polymorphism | Satu kontrak, banyak perilaku | Different notification senders |
| 15 | Composition | Menyusun perilaku dari bagian | Service receives a repository |
| 16 | Interface | Kontrak kemampuan | `send(message)` |
| 17 | Exception | Sinyal kegagalan eksekusi | Throw validation error |
| 18 | Promise | Representasi hasil asinkron mendatang | Await a network result |
| 19 | Event loop | Pengatur eksekusi pekerjaan pada host JS | Run callback after I/O |
| 20 | Garbage collection | Pengambilan kembali memori tak terjangkau | Free unreachable objects |
| 21 | Array | Koleksi berurutan dengan indeks | List of scores |
| 22 | Hash map | Pemetaan kunci ke nilai | Student ID to student |
| 23 | Set | Koleksi nilai unik | Deduplicate IDs |
| 24 | Stack | Struktur terakhir masuk pertama keluar | Undo history |
| 25 | Queue | Struktur pertama masuk pertama keluar | Pending jobs |
| 26 | Linked list | Rangkaian simpul yang saling merujuk | Pointer traversal |
| 27 | Tree | Struktur hierarkis tanpa siklus | Folder hierarchy |
| 28 | Graph | Simpul dan hubungan umum | Route network |
| 29 | Heap | Struktur prioritas; juga istilah area memori | Min-heap selects cheapest task |
| 30 | Big-O | Batas pertumbuhan biaya | Linear scan O(n) |
| 31 | Primary key | Identitas unik baris | Employee ID |
| 32 | Foreign key | Referensi yang menjaga integritas antarbaris | Attendance → student |
| 33 | Unique constraint | Batasan tidak boleh duplikat | One event ID per device |
| 34 | Normalization | Pengaturan fakta untuk mengurangi anomali | Separate department table |
| 35 | Join | Penggabungan baris menurut kondisi | Employee and department |
| 36 | Aggregation | Peringkasan beberapa baris | Count attendance |
| 37 | Window function | Perhitungan kelompok tanpa merangkum baris | Rank salaries |
| 38 | CTE | Ekspresi tabel bernama dalam query | `WITH totals AS (...)` |
| 39 | Index | Struktur akses untuk pencarian | B-tree on date |
| 40 | Query plan | Strategi eksekusi query | Inspect scan versus index |
| 41 | Transaction | Unit perubahan atomik | Order plus stock movement |
| 42 | Atomicity | Semua perubahan berhasil atau batal | No half-written transfer |
| 43 | Isolation | Pengaturan pengaruh transaksi bersamaan | Avoid lost updates |
| 44 | Durability | Hasil commit bertahan sesuai jaminan sistem | Recover committed records |
| 45 | Deadlock | Transaksi saling menunggu kunci | Retry a selected victim |
| 46 | Migration | Perubahan skema/data berversi | Add nullable column first |
| 47 | Pagination | Pembagian hasil menjadi halaman | Cursor after last ID |
| 48 | N+1 query | Satu query awal ditambah query per objek | Fetch students once, not per row |
| 49 | Soft delete | Menandai terhapus tanpa langsung membuang | `deleted_at` timestamp |
| 50 | Upsert | Insert atau update saat konflik | Deduplicate attendance |
| 51 | HTTP | Protokol permintaan/respons web | Browser requests a resource |
| 52 | REST | Gaya arsitektur berbasis resource dan batasan | Resource representations |
| 53 | Endpoint | Alamat operasi API | `/students/12` |
| 54 | Status code | Kode hasil respons | 201 Created |
| 55 | Idempotency | Efek pengulangan sama dengan sekali | Retry payment key |
| 56 | Cookie | Data yang dikirim browser sesuai aturan | Session identifier |
| 57 | Session | Konteks autentikasi berjangka | Revoke a login |
| 58 | JWT | Format token klaim yang dapat ditandatangani | Verify issuer and expiry |
| 59 | CORS | Aturan akses lintas origin di browser | Allow selected web origin |
| 60 | Webhook | Panggilan balik HTTP saat kejadian | Payment notification |
| 61 | Authentication | Pembuktian identitas | Sign in |
| 62 | Authorization | Pemeriksaan izin tindakan dan objek | Mentor owns this class |
| 63 | RBAC | Izin berdasar peran | Admin versus mentor |
| 64 | Least privilege | Memberi izin minimum yang diperlukan | Read-only reporting user |
| 65 | Encryption | Penyandian yang bisa dibalik dengan kunci | TLS protects transit |
| 66 | Password hashing | Transformasi lambat untuk verifikasi sandi | Argon2id with salt |
| 67 | SQL injection | Input memengaruhi struktur query | Prevent with parameters |
| 68 | XSS | Eksekusi skrip penyerang di konteks situs | Escape untrusted HTML |
| 69 | CSRF | Permintaan tidak diinginkan memakai sesi korban | Protect cookie-authenticated writes |
| 70 | Audit trail | Jejak perubahan yang dapat ditelusuri | Who changed a grade |
| 71 | Unit test | Pengujian logika kecil terisolasi | Grade rounding rule |
| 72 | Integration test | Pengujian interaksi antarkomponen | Real database constraint |
| 73 | E2E test | Pengujian alur pengguna menyeluruh | Login to report export |
| 74 | Regression test | Pengaman agar bug lama tidak kembali | Replay duplicate callback |
| 75 | Mock | Pengganti terkontrol suatu dependensi | Fake payment response |
| 76 | Boundary test | Pengujian nilai di sekitar batas | Capacity zero and one |
| 77 | Observability | Kemampuan memahami keadaan dari keluaran | Logs, metrics and traces |
| 78 | Log | Catatan kejadian | Failed request ID |
| 79 | Metric | Ukuran numerik sepanjang waktu | Error rate |
| 80 | Trace | Jejak satu pekerjaan lintas komponen | API to database spans |
| 81 | Requirement | Kebutuhan yang disepakati | Mentor may correct attendance |
| 82 | Acceptance criterion | Kondisi konkret penerimaan | Duplicate scan creates one record |
| 83 | Backlog | Daftar kerja yang diurutkan | Prioritised feature list |
| 84 | Sprint | Periode kerja Scrum | Inspect increment at review |
| 85 | Retrospective | Refleksi proses dan perbaikan | Reduce review delays |
| 86 | Code review | Pemeriksaan perubahan oleh rekan | Find missing permission check |
| 87 | Merge | Menggabungkan riwayat perubahan | Integrate feature branch |
| 88 | Rebase | Memutar ulang commit di atas basis baru | Update private branch |
| 89 | CI | Integrasi dengan validasi otomatis | Run tests on change |
| 90 | Technical debt | Biaya masa depan akibat pilihan saat ini | Document deferred refactor |
| 91 | Container | Paket proses dengan isolasi OS | Docker application image |
| 92 | Virtual machine | Mesin virtual dengan OS tamu | Cloud server instance |
| 93 | Load balancer | Pembagi permintaan ke beberapa backend | Route to healthy instance |
| 94 | Cache | Salinan untuk mempercepat akses | Tenant-scoped report cache |
| 95 | Message broker | Perantara pengiriman pesan | Retry export jobs |
| 96 | Monolith | Aplikasi sebagai satu unit deployment | Modular small business app |
| 97 | Microservice | Layanan terpisah dengan batas dan operasi sendiri | Independently deployed domain |
| 98 | Backup | Salinan untuk pemulihan | Restore a database snapshot |
| 99 | RPO | Batas kehilangan data yang disepakati | Maximum acceptable data gap |
| 100 | RTO | Target waktu pemulihan | Time to restore service |
