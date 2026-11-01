# 04 — Programming Fundamentals

**Purpose:** Answer core concept questions correctly; use hypothetical examples unless an actual implementation is confirmed.
**Created:** 31 October 2026
**Items:** 20 (FUND-01 … FUND-20)
**Schema:** `_SCHEMA.md`
**Candidate for:** Marchel Karuna Kwee — PT Amber Solusi Internasional, Fresh Graduate Programmer, 2 November 2026

**Difficulty mix:** Foundation 8 · Intermediate 8 · Advanced 4

**Grounding:** Technical explanations are general knowledge. Where an answer needs an example, it uses only fact-sheet material (`../sources/candidate_fact_sheet.md`). No answer claims Java, C#, .NET, Angular, Flutter, Spring, Oracle, Odoo, or SAP experience — those are handled as gap, transferable skill, and plan.

**Evidence boundary:** Stack names support exposure, not a specific bug, schema, architecture or learning habit. Examples below are general practice unless explicitly documented.

---

### Q-FUND-01 — Data types

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | Type systems |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | What are data types, and why does a language care which one you use? |
| **Pertanyaan (ID)** | Apa itu tipe data, dan mengapa bahasa pemrograman memperdulikan tipe yang Anda pakai? |
| **What is assessed** | Whether you understand that types define valid operations and memory shape, not just a label. |
| **Evidence basis** | General knowledge; example from fact sheet §3.1 (TypeScript, PostgreSQL, attendance status). |
| **Strong answer outline** | • A type is the set of values plus the allowed operations<br>• Primitives versus composites<br>• Static versus dynamic checking<br>• Why it matters: wrong type, wrong meaning — "1" plus 1 |
| **Model answer (EN)** | A type describes valid values and operations. JavaScript can coerce values, so a string plus a number may concatenate rather than add. TypeScript adds static checks, but its types are erased and do not validate an external payload at runtime. A database can also enforce types and constraints. For a hypothetical attendance status, I would consider an explicit allowed-value constraint; that is a proposed example, not a claim about my actual schema. |
| **Contoh jawaban (ID)** | Tipe menjelaskan nilai dan operasi yang valid. JavaScript dapat mengonversi nilai secara implisit, sehingga string ditambah angka bisa menjadi penggabungan, bukan penjumlahan. TypeScript menambahkan pemeriksaan statis, tetapi tipenya dihapus dan tidak memvalidasi payload eksternal saat runtime. Basis data juga dapat menegakkan tipe serta constraint. Untuk contoh absensi hipotetis saya mempertimbangkan batasan nilai status; itu usulan, bukan klaim tentang skema asli proyek saya. |
| **Follow-up** | What is the difference between `null` and `undefined` in JavaScript? |
| **Weak answer / red flag** | "Types are int, string, boolean" recited with no explanation of operations or checking. |
| **Scoring anchor** | 1 = list of type names only · 3 = correct definition, no consequence · 5 = values plus operations, static versus dynamic, and a real bug class it prevents |

---

### Q-FUND-02 — Value versus reference

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | Memory semantics |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | JavaScript passes values. How does copying an object reference differ from copying an object? |
| **Pertanyaan (ID)** | JavaScript melewatkan nilai. Apa bedanya menyalin referensi objek dan menyalin objek itu sendiri? |
| **What is assessed** | Whether you can predict aliasing bugs instead of discovering them. |
| **Evidence basis** | General knowledge; example from fact sheet §3.1 (React/Next.js state, TypeScript). |
| **Strong answer outline** | • Primitives are copied on assignment<br>• Objects and arrays copy the reference, not the contents<br>• Mutation through one name is visible through the other<br>• Fix: copy deliberately, or do not mutate |
| **Model answer (EN)** | JavaScript arguments are passed by value, including values that are object references. Two copied reference values can point to the same object, so mutation is visible through both. Reassigning the parameter itself does not reassign the caller's variable. A shallow object copy still shares nested objects. In a hypothetical React example, mutating state in place can defeat change detection; I would create the appropriate new references rather than claim this was a personal bug. |
| **Contoh jawaban (ID)** | Argumen JavaScript dilewatkan sebagai nilai, termasuk nilai berupa referensi objek. Dua nilai referensi salinan dapat menunjuk objek sama sehingga mutasi terlihat melalui keduanya. Penugasan ulang parameter tidak mengganti variabel pemanggil. Salinan objek dangkal tetap berbagi objek bersarang. Dalam contoh React hipotetis, mutasi state langsung dapat mengganggu deteksi perubahan; saya membuat referensi baru pada tingkat yang sesuai, bukan mengklaim ini bug pribadi yang pernah terjadi. |
| **Follow-up** | Why does mutating state in place break React's re-render? |
| **Weak answer / red flag** | "Objects are passed by reference" with no mention of copying or aliasing consequences. |
| **Scoring anchor** | 1 = confused or reversed explanation · 3 = correct rule, no example of the failure · 5 = correct semantics, a concrete aliasing bug, and the remedy |

---

### Q-FUND-03 — Four pillars of OOP

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | OOP |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | Give me the four pillars of object-oriented programming, and one sentence on why each exists. |
| **Pertanyaan (ID)** | Sebutkan empat pilar pemrograman berorientasi objek, dan satu kalimat tentang alasan masing-masing ada. |
| **What is assessed** | Whether you understand purpose rather than memorised labels. |
| **Evidence basis** | General knowledge; fact sheet §3.6 (Nitro Itera Racing, Python and Pygame, OOP applied). |
| **Strong answer outline** | • Encapsulation: hide state, expose behaviour<br>• Abstraction: name the concept, not the steps<br>• Inheritance: share a contract or common behaviour<br>• Polymorphism: same call, different behaviour per type |
| **Model answer (EN)** | Encapsulation controls access to state so operations can protect invariants. Abstraction exposes a useful contract while hiding unnecessary details. Inheritance specialises an existing type, and polymorphism lets different implementations respond through one contract. My portfolio documents OOP use in a Python/Pygame game, but not the exact class design. A general example would be different game entities implementing an update operation; I would verify the actual code before presenting that example as my implementation. |
| **Contoh jawaban (ID)** | Enkapsulasi mengendalikan akses ke state agar operasi menjaga aturan. Abstraksi menampilkan kontrak yang berguna sambil menyembunyikan detail tidak perlu. Pewarisan mengkhususkan tipe yang sudah ada, sedangkan polimorfisme memungkinkan implementasi berbeda merespons lewat satu kontrak. Portofolio mencatat OOP dalam game Python/Pygame, tetapi tidak merinci desain kelas. Contoh umum adalah entitas game dengan operasi update; saya memeriksa kode asli sebelum mengaku contoh itu implementasi saya. |
| **Follow-up** | Which of the four do you actually use most in web development? |
| **Weak answer / red flag** | Naming four words with textbook definitions in the wrong order; or listing "classes, objects, methods, properties" as the pillars. |
| **Scoring anchor** | 1 = wrong or missing pillars · 3 = four correct definitions, no purpose · 5 = four correct purposes, a stated preference, and one real example |

---

### Q-FUND-04 — Interface versus abstract class

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | OOP |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | When would you use an interface, and when is an abstract class the better tool? |
| **Pertanyaan (ID)** | Kapan Anda memakai interface, dan kapan abstract class lebih tepat? |
| **What is assessed** | Whether you can choose a construct by its constraints rather than by habit. |
| **Evidence basis** | General knowledge; fact sheet §5 (TypeScript), §3.1. |
| **Strong answer outline** | Contract versus shared state/implementation; language-specific rules; TypeScript erasure; modern Java/C# default methods. |
| **Model answer (EN)** | I would use an interface to describe a capability or contract, and an abstract class when related types genuinely share state and implementation. The exact rules depend on the language: modern Java and C# interfaces can include some implementation, so saying interfaces never contain code is too broad. TypeScript interfaces are erased and provide no runtime validation. I would choose by the relationship and required behaviour, not claim a personal preference unsupported by project evidence. |
| **Contoh jawaban (ID)** | Saya memakai interface untuk menjelaskan kemampuan atau kontrak, dan abstract class ketika tipe terkait memang berbagi state serta implementasi. Aturan tepat bergantung bahasa: interface Java dan C# modern dapat memuat sebagian implementasi, sehingga pernyataan bahwa interface tidak pernah memiliki kode terlalu mutlak. Interface TypeScript dihapus dan tidak memvalidasi runtime. Pilihan didasarkan pada hubungan serta perilaku yang diperlukan, bukan preferensi pribadi yang belum didukung bukti proyek. |
| **Follow-up** | In a language with no interfaces, what would you use instead? |
| **Weak answer / red flag** | "They are the same thing"; or claiming interfaces hold implementation in every language. |
| **Scoring anchor** | 1 = conflates the two · 3 = correct definitions, no decision rule · 5 = definitions plus a selection rule, and awareness of how it differs by language |

---

### Q-FUND-05 — Composition over inheritance

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | Design |
| **Difficulty** | Advanced |
| **Asked in** | Technical |
| **Question (EN)** | People say prefer composition over inheritance. Do you agree, and where is the line? |
| **Pertanyaan (ID)** | Banyak yang bilang utamakan komposisi daripada pewarisan. Anda setuju, dan di mana batasnya? |
| **What is assessed** | Whether you can hold a heuristic without applying it mechanically. |
| **Evidence basis** | General knowledge; fact sheet §3.1 (three overlapping roles in one application). |
| **Strong answer outline** | • The problem inheritance causes: fragile base class, forced hierarchy<br>• Composition: behaviour assembled, replaced at runtime<br>• Where inheritance is right: true is-a with a shared invariant<br>• Example: permissions as composable checks, not subclasses of user<br>• Cost of composition: more pieces, more indirection |
| **Model answer (EN)** | Composition is a useful default when behaviour varies independently, because collaborators can change without forcing a fragile class hierarchy. Inheritance can still be appropriate when subtypes honour a genuine shared contract. For a hypothetical role system, I would consider permissions as policies rather than one subclass per role, especially if roles overlap. That is general reasoning, not evidence of my actual permission implementation. Composition also adds indirection, so I would keep the design as simple as the need allows. |
| **Contoh jawaban (ID)** | Komposisi merupakan pilihan awal yang berguna ketika perilaku bervariasi secara mandiri, karena bagian dapat berubah tanpa hierarki kelas rapuh. Pewarisan tetap tepat jika subtipe benar-benar memenuhi kontrak bersama. Untuk sistem peran hipotetis, saya mempertimbangkan izin sebagai kebijakan, bukan subclass per peran, terutama jika peran tumpang tindih. Itu penalaran umum, bukan bukti implementasi izin saya. Komposisi juga menambah perantara, sehingga desain tetap dibuat sesederhana kebutuhan. |
| **Follow-up** | What evidence would you inspect before describing the project's actual permission design? |
| **Weak answer / red flag** | Reciting the slogan with no example; or the opposite absolutism, "inheritance is always wrong". |
| **Scoring anchor** | 1 = slogan only · 3 = agrees with a general reason · 5 = names the failure mode, applies it to real code, states the exception, and admits the cost |

---

### Q-FUND-06 — Stack versus heap

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | Memory |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | What lives on the stack and what lives on the heap, and why should a web developer care? |
| **Pertanyaan (ID)** | Apa yang tersimpan di stack dan apa di heap, dan mengapa web developer perlu peduli? |
| **What is assessed** | Whether you understand allocation and lifetime at a level that explains real failures. |
| **Evidence basis** | General knowledge; fact sheet §5 (JavaScript, PHP, C++). |
| **Strong answer outline** | • Stack: call frames, locals, return addresses; automatic and fast<br>• Heap: objects whose lifetime outlives the call; managed or manual<br>• Stack overflow from deep recursion; heap growth from accumulation<br>• Why it matters: memory leaks are retained references, not "full memory" |
| **Model answer (EN)** | The call stack tracks active function frames; deep recursion can exhaust it. Heap allocation supports objects with lifetimes that may extend beyond one call, but exact placement depends on the language and runtime optimisations. JavaScript uses managed memory, while C++ also has automatic lifetime and RAII, not only manual allocation. I would care about retained references, unbounded caches and recursion depth, and use measurements rather than assume every growing process has the same cause. |
| **Contoh jawaban (ID)** | Call stack melacak frame fungsi aktif; rekursi terlalu dalam dapat menghabiskannya. Alokasi heap mendukung objek dengan masa hidup yang dapat melewati satu pemanggilan, tetapi lokasi tepat bergantung bahasa serta optimasi runtime. JavaScript memakai memori terkelola, sedangkan C++ juga memiliki masa hidup otomatis dan RAII, bukan hanya alokasi manual. Saya memperhatikan referensi tertahan, cache tak terbatas dan kedalaman rekursi, lalu mengukur penyebab pertumbuhan proses daripada menyamakannya semua. |
| **Follow-up** | If a Node process grows over three days, what would you inspect? |
| **Weak answer / red flag** | "Stack is small, heap is big" as the whole answer, with no lifetime or allocation model. |
| **Scoring anchor** | 1 = size comparison only · 3 = correct contents, no consequence · 5 = contents, lifetime, management model, and a real failure it explains |

---

### Q-FUND-07 — Immutability

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | State management |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | What does immutability mean in practice, and what does it cost you? |
| **Pertanyaan (ID)** | Apa arti immutability dalam praktik, dan apa biayanya? |
| **What is assessed** | Whether you can name both the benefit and the price instead of treating it as a rule to obey. |
| **Evidence basis** | General knowledge; fact sheet §3.1 (React state), §5 (TypeScript). |
| **Strong answer outline** | • No mutation after creation; produce a new value instead<br>• Benefit: predictable comparisons, safe sharing, easier debugging<br>• Cost: allocation and copying, especially for large structures<br>• `const` is not immutability — it only fixes the binding |
| **Model answer (EN)** | It means a value does not change after it is created; you produce a new one instead. The benefit is that reasoning gets local: if nothing mutates, a value you checked is still valid later, comparisons are cheap because identity tells you whether something changed, and sharing is safe. React depends on that, which is why updating state means returning a new object. The cost is allocation and copying, and for a large nested structure a naive copy is expensive. Worth saying: `const` in JavaScript is not immutability, it only stops reassignment of the name. |
| **Contoh jawaban (ID)** | Artinya sebuah nilai tidak berubah setelah dibuat; Anda menghasilkan nilai baru. Manfaatnya penalaran menjadi lokal: kalau tidak ada mutasi, nilai yang sudah diperiksa tetap valid nanti, perbandingan jadi murah karena identitas menunjukkan perubahan, dan berbagi data menjadi aman. React bergantung pada itu, karena itu memperbarui state berarti mengembalikan objek baru. Biayanya alokasi dan penyalinan, dan untuk struktur bersarang yang besar, penyalinan naif mahal. Perlu dicatat: `const` di JavaScript bukan immutability, ia hanya mencegah penugasan ulang nama. |
| **Follow-up** | When is copying on every update a bad trade? |
| **Weak answer / red flag** | "Immutable means I use const"; or claiming immutability is free. |
| **Scoring anchor** | 1 = confuses const with immutability · 3 = correct meaning, no cost · 5 = meaning, one concrete benefit in code you wrote, and an honest cost |

---

### Q-FUND-08 — Async, event loop, callbacks and promises

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | Concurrency |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | JavaScript is single-threaded. So how does it handle a slow database call without freezing everything? |
| **Pertanyaan (ID)** | JavaScript berjalan single-thread. Lalu bagaimana menangani query basis data yang lambat tanpa membekukan semuanya? |
| **What is assessed** | Whether you understand the event loop well enough to explain latency, not just use `await`. |
| **Evidence basis** | General knowledge; fact sheet §5 (Node.js), §3.1 (Next.js server routes). |
| **Strong answer outline** | • One call stack; async work is handed to the platform<br>• Event loop: run stack, drain microtasks, take next task<br>• Callback: continuation passed in; nesting becomes unreadable<br>• Promise: a value for a future result, chainable, with one error path<br>• `async/await` is syntax over promises, still non-blocking |
| **Model answer (EN)** | It delegates. The call stack runs one thing at a time, but a database call is handed to the platform, and the callback is queued when the result arrives. The event loop keeps taking work from the queue when the stack is empty. Callbacks work, but nesting them for several dependent steps makes the order hard to read. A promise represents a future value, so you chain steps and handle errors in one place. `async` and `await` are syntax over promises: the function pauses at the await, but the thread is free, so other requests continue. It is still single-threaded — a long synchronous loop blocks everything. |
| **Contoh jawaban (ID)** | Ia mendelegasikan. Call stack hanya menjalankan satu hal, tetapi query basis data diserahkan ke platform, dan callback dimasukkan ke antrean saat hasilnya tiba. Event loop terus mengambil pekerjaan dari antrean ketika stack kosong. Callback berfungsi, tetapi menyusunnya bersarang untuk beberapa langkah berurutan membuat urutannya sulit dibaca. Promise mewakili nilai masa depan, sehingga Anda merangkai langkah dan menangani error di satu tempat. `async` dan `await` adalah sintaks di atas promise: fungsi berhenti di await, tetapi thread tetap bebas, jadi permintaan lain berjalan. Tetap single-thread — perulangan sinkron yang panjang memblokir semuanya. |
| **Follow-up** | What is the difference between the microtask queue and the task queue, and why does it matter? |
| **Weak answer / red flag** | "JavaScript is multithreaded"; or "await blocks the thread until it finishes". |
| **Scoring anchor** | 1 = says it runs in parallel threads · 3 = correct high-level story, no error or blocking nuance · 5 = delegation, event loop order, callback-to-promise progression, and the synchronous-blocking caveat |

---

### Q-FUND-09 — GET versus POST

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | HTTP |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | What is the real difference between GET and POST, beyond "one puts data in the URL"? |
| **Pertanyaan (ID)** | Apa perbedaan nyata GET dan POST, selain "yang satu menaruh data di URL"? |
| **What is assessed** | Whether you understand semantics, safety, and caching rather than transport trivia. |
| **Evidence basis** | General knowledge; fact sheet §3.1 (attendance records), §3.2 (data operations). |
| **Strong answer outline** | • GET retrieves and is safe and idempotent<br>• POST submits and changes state; not idempotent<br>• Consequences: caching, bookmarks, retries, logs<br>• Never put secrets in a URL, because URLs are logged |
| **Model answer (EN)** | GET requests retrieval and is safe and idempotent by HTTP semantics; incidental logging does not violate that intended-effect definition. POST asks a resource to process submitted data and is not guaranteed to be safe or idempotent. A particular POST can still implement deduplication. I would choose methods by meaning, not whether parameters are visible, and keep secrets out of URLs. HTTPS and authorization are needed regardless of the chosen method. |
| **Contoh jawaban (ID)** | GET meminta pengambilan dan bersifat safe serta idempoten menurut semantik HTTP; pencatatan log sampingan tidak melanggar definisi efek yang dimaksud itu. POST meminta resource memproses data dan tidak dijamin safe atau idempoten. Implementasi POST tertentu tetap dapat melakukan deduplikasi. Saya memilih metode berdasarkan makna, bukan visibilitas parameter, serta menjauhkan rahasia dari URL. HTTPS dan otorisasi diperlukan untuk kedua metode tersebut. |
| **Follow-up** | How would you stop a double-submitted POST from creating two records? |
| **Weak answer / red flag** | "GET is less secure than POST" as the whole answer; or claiming POST hides data from logs. |
| **Scoring anchor** | 1 = only transport-level differences · 3 = correct safety distinction, no consequences · 5 = semantics, consequences for caching and retries, and a security rule about URLs |

---

### Q-FUND-10 — 401 versus 403

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | HTTP status codes |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | A user complains they "cannot access the page". How do 401 and 403 tell you different things? |
| **Pertanyaan (ID)** | Seorang pengguna mengeluh "tidak bisa mengakses halaman". Bagaimana 401 dan 403 memberi informasi berbeda? |
| **What is assessed** | Whether you can diagnose from status codes instead of guessing. |
| **Evidence basis** | General knowledge; fact sheet §3.1 (student, mentor, admin roles). |
| **Strong answer outline** | 401 missing/invalid credentials with challenge; 403 refusal not proof of known identity; optional concealed 404. |
| **Model answer (EN)** | A 401 response means the request lacks valid authentication credentials and should include a WWW-Authenticate challenge. A 403 means the server refuses the action; it often reflects insufficient permission, but does not universally prove identity was established. In a proposed role-based application, re-authentication should not be offered as the fix for a genuinely forbidden action. For sensitive objects, an agreed 404 response can avoid disclosing existence. I would inspect the actual authorization path. |
| **Contoh jawaban (ID)** | Respons 401 berarti permintaan tidak mempunyai kredensial autentikasi valid dan seharusnya menyertakan tantangan WWW-Authenticate. Respons 403 berarti server menolak tindakan; sering terkait izin, tetapi tidak selalu membuktikan identitas sudah diketahui. Dalam aplikasi berbasis peran yang diusulkan, autentikasi ulang bukan solusi untuk tindakan yang memang dilarang. Untuk objek sensitif, kebijakan 404 dapat menghindari pengungkapan keberadaan. Saya tetap memeriksa jalur otorisasi yang sebenarnya. |
| **Follow-up** | Which one would you log as a security signal, and why? |
| **Weak answer / red flag** | "401 is not logged in, 403 is forbidden" recited with no diagnosis or consequence. |
| **Scoring anchor** | 1 = reversed definitions · 3 = correct definitions only · 5 = definitions, the user-facing consequence, a real role example, and the 404 disclosure nuance |

---

### Q-FUND-11 — REST

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | API design |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | What makes an API RESTful, and where does that style get in the way? |
| **Pertanyaan (ID)** | Apa yang membuat sebuah API disebut RESTful, dan di mana gaya itu justru menyulitkan? |
| **What is assessed** | Whether you can describe a style and its limits rather than reciting "it uses JSON". |
| **Evidence basis** | General knowledge; fact sheet §3.1 (attendance resources), §1 (links). |
| **Strong answer outline** | • Resources as nouns, addressed by URL<br>• HTTP verbs carry the operation<br>• Statelessness: each request carries its context<br> • Status codes and representations; versioning<br>• Friction: multi-step workflows and over-fetching |
| **Model answer (EN)** | REST is an architectural style with constraints including a uniform interface, stateless interaction, cacheability and client-server separation. Requests carry the context needed to interpret them; this does not mean the server cannot store resource state. HTTP resource APIs often use representations and meaningful methods, but JSON alone does not make an API RESTful. Complex workflows can be awkward to model, and some designs fetch more data or require more round trips than a screen needs. |
| **Contoh jawaban (ID)** | REST merupakan gaya arsitektur dengan batasan termasuk interface seragam, interaksi stateless, cacheability dan pemisahan client-server. Permintaan membawa konteks yang diperlukan untuk ditafsirkan; ini tidak berarti server dilarang menyimpan state resource. API HTTP sering menggunakan representasi dan metode bermakna, tetapi JSON saja tidak menjadikannya RESTful. Alur kompleks bisa sulit dimodelkan, dan beberapa desain mengambil data berlebih atau membutuhkan lebih banyak perjalanan jaringan daripada kebutuhan layar. |
| **Follow-up** | Is GraphQL the answer to the over-fetching problem? |
| **Weak answer / red flag** | "REST means JSON over HTTP"; or insisting REST is a protocol or a standard. |
| **Scoring anchor** | 1 = equates REST with JSON · 3 = correct principles, no limits · 5 = principles, statelessness rationale, and honest friction with a non-resource workflow |

---

### Q-FUND-12 — Idempotency

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | Reliability |
| **Difficulty** | Advanced |
| **Asked in** | Technical |
| **Question (EN)** | What does idempotent mean, and why would a payment or attendance system care more about it than a blog does? |
| **Pertanyaan (ID)** | Apa arti idempoten, dan mengapa sistem pembayaran atau absensi lebih peduli daripada blog? |
| **What is assessed** | Whether you can reason about retries and duplicate side effects, which is where juniors cause real damage. |
| **Evidence basis** | General knowledge; fact sheet §3.1 (RFID scans producing attendance records). |
| **Strong answer outline** | Same intended effect; response may differ; POST can implement safe retry with atomic key/payload validation; timeout ambiguity. |
| **Model answer (EN)** | Idempotency means repeated identical requests have the same intended effect as one request, not necessarily the same response code. GET, PUT and DELETE have idempotent semantics; POST is not guaranteed to, but can implement it. For a payment I would atomically associate a stable key and payload with the operation, reject conflicting reuse and return the stored outcome for a completed retry. Timeouts leave uncertainty, so reconciliation and pending-state handling still matter. |
| **Contoh jawaban (ID)** | Idempotensi berarti pengulangan permintaan identik mempunyai efek tujuan yang sama seperti sekali, bukan selalu kode respons sama. GET, PUT dan DELETE bersemantik idempoten; POST tidak dijamin, tetapi dapat mengimplementasikannya. Untuk pembayaran, kunci stabil dan payload dikaitkan secara atomik dengan operasi, penggunaan ulang yang bertentangan ditolak dan retry selesai mengembalikan hasil tersimpan. Timeout meninggalkan ketidakpastian, sehingga rekonsiliasi serta penanganan status pending tetap diperlukan. |
| **Follow-up** | Where would you store that key, and how long would you keep it? |
| **Weak answer / red flag** | Equates idempotency with read-only, or assumes all POST requests are idempotent without implementation guarantees. |
| **Scoring anchor** | 1 = confuses idempotent with safe or read-only · 3 = correct definition, no mechanism · 5 = definition, verb-by-verb accuracy, retry reality, and a concrete deduplication technique |

---

### Q-FUND-13 — Authentication versus authorization

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | Security |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | Authentication and authorization get used interchangeably. What is the difference, and where does each fail? |
| **Pertanyaan (ID)** | Autentikasi dan otorisasi sering dianggap sama. Apa bedanya, dan di mana masing-masing gagal? |
| **What is assessed** | Whether you can separate identity from permission when reasoning about a security bug. |
| **Evidence basis** | General knowledge; fact sheet §3.1 (three roles, one data model). |
| **Strong answer outline** | • Authentication: who you are; login, session, token<br>• Authorization: what you may do; roles, ownership, policy<br>• Common failure: authenticating once, then trusting the client<br>• Check authorization on every request, server-side |
| **Model answer (EN)** | Authentication establishes identity: you prove you are the account you claim, usually with a password, a session cookie, or a token. Authorization decides what that identity may do. They fail differently. If authentication fails, anyone can be anyone. If authorization fails, a legitimate user can reach data that is not theirs, which is quieter and more damaging. The classic mistake is checking the role in the browser and hiding a button, then leaving the server endpoint open. In a three-role application, every endpoint has to re-check, because the client is not a security boundary, it is a convenience. |
| **Contoh jawaban (ID)** | Autentikasi menetapkan identitas: Anda membuktikan bahwa Anda adalah akun yang diklaim, biasanya dengan kata sandi, cookie sesi, atau token. Otorisasi menentukan apa yang boleh dilakukan identitas itu. Keduanya gagal dengan cara berbeda. Kalau autentikasi gagal, siapa pun bisa menjadi siapa pun. Kalau otorisasi gagal, pengguna sah bisa mencapai data yang bukan miliknya, dan itu lebih senyap serta lebih merusak. Kesalahan klasiknya adalah memeriksa peran di peramban dan menyembunyikan tombol, lalu membiarkan endpoint server terbuka. Di aplikasi tiga peran, setiap endpoint harus memeriksa ulang, karena klien bukan batas keamanan, melainkan kenyamanan. |
| **Follow-up** | Where exactly would you put that check in a request, and why there? |
| **Weak answer / red flag** | Uses the words correctly but cannot name a failure mode; or says hiding the button is enough. |
| **Scoring anchor** | 1 = treats them as the same · 3 = correct definitions only · 5 = definitions, distinct failure modes, and the client-is-not-a-boundary principle |

---

### Q-FUND-14 — Hashing versus encryption

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | Security |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | Passwords are hashed, not encrypted. Why the distinction, and what makes a hash good for passwords? |
| **Pertanyaan (ID)** | Kata sandi di-hash, bukan dienkripsi. Mengapa dibedakan, dan apa yang membuat hash baik untuk kata sandi? |
| **What is assessed** | Whether you know which primitive belongs to which problem. |
| **Evidence basis** | General knowledge. No answer claims to have implemented an authentication system. |
| **Strong answer outline** | • Encryption is reversible with a key; hashing is one-way<br>• Passwords never need to be read back, only compared<br>• Salt: unique per user, defeats precomputed tables<br>• Deliberately slow algorithms: bcrypt, scrypt, Argon2<br>• Encryption is for data you must recover, plus TLS in transit |
| **Model answer (EN)** | Encryption is reversible: with the key you get the original back, which is what you want for a card number you must read later. A hash is one-way, so you cannot recover the input, which is exactly right for a password, because the system never needs to know it — only to check that a new attempt produces the same result. A good password hash is salted with a unique value per user, so identical passwords do not produce identical hashes, and deliberately slow, so guessing is expensive. bcrypt, scrypt, and Argon2 are built for that. A fast hash like SHA-256 is fine for integrity, not for passwords. |
| **Contoh jawaban (ID)** | Enkripsi bersifat reversibel: dengan kuncinya Anda mendapatkan kembali aslinya, yang Anda butuhkan untuk nomor kartu yang harus dibaca nanti. Hash bersifat satu arah, jadi masukannya tidak bisa dipulihkan, dan itu tepat untuk kata sandi karena sistem tidak perlu mengetahuinya — hanya perlu memastikan percobaan baru menghasilkan hasil yang sama. Hash kata sandi yang baik diberi salt unik per pengguna, sehingga kata sandi identik tidak menghasilkan hash identik, dan sengaja dibuat lambat agar menebak menjadi mahal. bcrypt, scrypt, dan Argon2 dirancang untuk itu. Hash cepat seperti SHA-256 cocok untuk integritas, bukan kata sandi. |
| **Follow-up** | If an attacker steals the database, what does the salt actually protect against? |
| **Weak answer / red flag** | "Hashing is a kind of encryption"; or proposing MD5 or SHA-256 for passwords. |
| **Scoring anchor** | 1 = treats hashing as encryption · 3 = correct one-way distinction, no salt or slowness · 5 = reversibility, salt purpose, slow-hash rationale, and the right primitive for the right job |

---

### Q-FUND-15 — SQL versus NoSQL

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | Data modelling |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | When would you choose a relational database over a document database? |
| **Pertanyaan (ID)** | Kapan Anda memilih basis data relasional dibanding basis data dokumen? |
| **What is assessed** | Whether the choice is driven by query shape and integrity, not fashion. |
| **Evidence basis** | Fact sheet §3.1 (PostgreSQL, Supabase), §3.4 (Firebase), §6.4. |
| **Strong answer outline** | • Relational: fixed shape, joins, constraints, transactions<br>• Document: flexible shape, aggregate reads, horizontal scale<br>• The deciding question: what questions will you ask of the data<br>• Mixed reality: Postgres with JSON columns |
| **Model answer (EN)** | I would choose from relationships, access patterns and integrity requirements. Relational databases are a useful default for joins, keys and transactional workflows; document models can suit aggregate-shaped access. Neither is universally faster or more scalable, and PostgreSQL can store JSON too. My documents list PostgreSQL, MySQL and Firebase, but Firebase is a platform with different database products. I should confirm which product was used before claiming a particular document-store implementation. |
| **Contoh jawaban (ID)** | Saya memilih berdasarkan hubungan, pola akses dan kebutuhan integritas. Basis data relasional menjadi pilihan berguna untuk join, kunci dan alur transaksional; model dokumen dapat sesuai untuk akses berbentuk agregat. Tidak ada yang selalu lebih cepat atau mudah diskalakan, dan PostgreSQL juga menyimpan JSON. Dokumen mencantumkan PostgreSQL, MySQL serta Firebase, tetapi Firebase memiliki beberapa produk basis data. Produk yang dipakai perlu dikonfirmasi sebelum mengklaim implementasi dokumen tertentu. |
| **Follow-up** | What would you lose if you moved the attendance data to a document store? |
| **Weak answer / red flag** | "SQL is for small data, NoSQL is for big data"; or claiming NoSQL has no schema, which is false in practice. |
| **Scoring anchor** | 1 = size-based or slogan answer · 3 = correct trade-off list, no deciding rule · 5 = a query-shape rule, both databases used as evidence, and the hybrid nuance |

---

### Q-FUND-16 — Compiled versus interpreted

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | Language execution |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | What actually differs between a compiled and an interpreted language, and is the line still clean? |
| **Pertanyaan (ID)** | Apa bedanya bahasa terkompilasi dan terinterpretasi, dan apakah batasnya masih jelas? |
| **What is assessed** | Whether you know the model beyond the label, including where it has blurred. |
| **Evidence basis** | General knowledge; fact sheet §5 (JavaScript, PHP, Python, C++). |
| **Strong answer outline** | • Compiled: translated ahead of time to machine code or bytecode<br>• Interpreted: read and executed by a runtime<br>• Trade-off: early error detection and speed versus portability and startup<br>• Blurred: JIT, bytecode, transpilation |
| **Model answer (EN)** | Compilation translates a program into another form, such as machine code or bytecode; interpretation executes a representation through a runtime. Many implementations combine both, including just-in-time compilation. CPython commonly compiles source to bytecode, while JVM implementations can compile hot code to machine instructions. Static typing and error detection are separate design choices, not automatic consequences of compilation. I would discuss the actual implementation rather than label every language permanently fast or slow. |
| **Contoh jawaban (ID)** | Kompilasi menerjemahkan program ke bentuk lain seperti kode mesin atau bytecode; interpretasi mengeksekusi representasi melalui runtime. Banyak implementasi menggabungkan keduanya, termasuk kompilasi just-in-time. CPython umumnya mengompilasi sumber menjadi bytecode, sedangkan implementasi JVM dapat mengompilasi bagian sering dipakai menjadi instruksi mesin. Pengetikan statis dan deteksi kesalahan adalah pilihan terpisah, bukan akibat otomatis kompilasi. Saya membahas implementasi nyata, bukan memberi label bahasa selalu cepat atau lambat. |
| **Follow-up** | Where does TypeScript sit in that picture? |
| **Weak answer / red flag** | "Compiled means fast, interpreted means slow" with no mention of when translation happens. |
| **Scoring anchor** | 1 = speed labels only · 3 = correct timing distinction, no trade-off · 5 = timing, trade-off, and at least one real hybrid example such as JVM or JIT |

---

### Q-FUND-17 — Java versus JavaScript

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | Language literacy |
| **Difficulty** | Foundation |
| **Asked in** | Technical |
| **Question (EN)** | Our projects use Java in places and JavaScript in others. Are they related at all? |
| **Pertanyaan (ID)** | Sebagian proyek kami memakai Java dan sebagian JavaScript. Apakah keduanya berhubungan? |
| **What is assessed** | Whether you can be accurate about a language you have not used without pretending or dismissing it. |
| **Evidence basis** | Fact sheet §5 (JavaScript, TypeScript listed; Java not listed); §10 (Java coursework unknown). |
| **Strong answer outline** | • Unrelated languages; the name is marketing history<br>• Java: static, class-based, JVM, enterprise backends<br>• JavaScript: dynamic, prototype-based, event loop, browser and Node<br>• Honest position: no Java project experience; the transferable parts are OOP and types |
| **Model answer (EN)** | No, they are unrelated, and the similar name is a historical marketing decision. Java is statically typed, class-based, and runs on the JVM, which is why it dominates large enterprise backends. JavaScript is dynamically typed, prototype-based, and built around the event loop; it runs in browsers and on Node. The syntax looks superficially alike, and both are object-oriented, but the execution models and ecosystems are different. I should be clear that I have no Java project experience. What would transfer is OOP structure, typing discipline from TypeScript, and general backend reasoning, not Java specifics. |
| **Contoh jawaban (ID)** | Tidak, keduanya tidak berhubungan, dan nama yang mirip adalah keputusan pemasaran historis. Java bertipe statis, berbasis kelas, dan berjalan di JVM, itulah sebabnya ia dominan di backend enterprise besar. JavaScript bertipe dinamis, berbasis prototipe, dan dibangun di sekitar event loop; ia berjalan di peramban dan di Node. Sintaksnya mirip sekilas, dan keduanya berorientasi objek, tetapi model eksekusi serta ekosistemnya berbeda. Saya perlu jelas bahwa saya belum punya pengalaman proyek Java. Yang bisa terbawa adalah struktur OOP, disiplin tipe dari TypeScript, dan penalaran backend umum, bukan hal spesifik Java. |
| **Follow-up** | If you had to write a Java service next month, what would you need to learn first? |
| **Weak answer / red flag** | "They are the same, one is for the web"; or claiming Java experience from a single course. |
| **Scoring anchor** | 1 = confuses or claims Java experience · 3 = correct separation, no execution model · 5 = accurate contrast, honest gap, and a precise statement of what transfers |

---

### Q-FUND-18 — Garbage collection

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | Memory management |
| **Difficulty** | Intermediate |
| **Asked in** | Technical |
| **Question (EN)** | How does garbage collection work, and can you still have a memory leak in a garbage-collected language? |
| **Pertanyaan (ID)** | Bagaimana garbage collection bekerja, dan apakah kebocoran memori masih mungkin di bahasa dengan GC? |
| **What is assessed** | Whether you understand reachability, and whether you know GC is not a substitute for ownership. |
| **Evidence basis** | General knowledge; fact sheet §5 (JavaScript, PHP, C++). |
| **Strong answer outline** | • GC finds objects no longer reachable from roots<br>• Mark and sweep; generational collection for short-lived objects<br>• Pauses are the cost; tuning is a trade-off<br>• Leaks persist when references are retained: caches, listeners, globals |
| **Model answer (EN)** | The collector starts from roots — globals, the stack, active closures — marks everything reachable, and reclaims what is not. Most runtimes are generational, because most objects die young, so they collect the young area often and the old area rarely. The cost is pause time, which is why tuning exists. And yes, you can still leak: a leak means memory that stays reachable but useless. A cache that never evicts, a listener never removed, or an array that only grows will all hold objects alive. The collector is correct about reachability, not about intent, so ownership still matters. |
| **Contoh jawaban (ID)** | Pengumpul mulai dari akar — variabel global, stack, closure aktif — menandai semua yang terjangkau, dan mengambil kembali yang tidak. Sebagian besar runtime bersifat generasional karena mayoritas objek mati muda, sehingga area muda dikumpulkan sering dan area tua jarang. Biayanya waktu jeda, itulah sebabnya ada penyetelan. Dan ya, kebocoran tetap mungkin: kebocoran berarti memori yang tetap terjangkau tetapi tidak berguna. Cache yang tidak pernah dibersihkan, listener yang tidak dilepas, atau array yang hanya bertambah akan menahan objek tetap hidup. Pengumpul benar soal keterjangkauan, bukan soal niat, jadi kepemilikan tetap penting. |
| **Follow-up** | Name one way a Node service leaks memory without ever throwing an error. |
| **Weak answer / red flag** | "GC means I never need to think about memory"; or describing GC as freeing objects you still reference. |
| **Scoring anchor** | 1 = "it deletes unused variables" · 3 = reachability explained, no leak nuance · 5 = reachability, generational idea, pause cost, and a credible retained-reference leak |

---

### Q-FUND-19 — Learning C# and .NET

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | Learning plan |
| **Difficulty** | Advanced |
| **Asked in** | Technical |
| **Question (EN)** | If this role needed C# and .NET, and you have never written either, what would your first month look like? |
| **Pertanyaan (ID)** | Kalau peran ini membutuhkan C# dan .NET, sementara Anda belum pernah menulis keduanya, seperti apa bulan pertama Anda? |
| **What is assessed** | Whether the plan is concrete, sequenced, and honest about what cannot be compressed. |
| **Evidence basis** | No documented C#/.NET project; PHP/TypeScript exposure documented; learning method below is a proposal, not a past habit. |
| **Strong answer outline** | No documented C#/.NET project; confirm any extra exposure; transferable concepts; small reviewed task; adapt learning checkpoints to team needs. |
| **Model answer (EN)** | I have not written C# or .NET, so I would not pretend the first month is free. What transfers is real: static typing from TypeScript, object-oriented structure, HTTP and REST, SQL, Git, and debugging habits. My plan would be two weeks on the language itself — types, generics, LINQ, async and await — by writing small console programs rather than watching videos. Then two weeks building one small ASP.NET Core API with Entity Framework against a schema I understand, so I meet dependency injection and migrations in context. After that I would read the team's code and ship one small reviewed change, and ask for their conventions in week one. |
| **Contoh jawaban (ID)** | Saya belum pernah menulis C# atau .NET, jadi saya tidak akan berpura-pura bulan pertama itu gratis. Yang bisa terbawa nyata: pengetikan statis dari TypeScript, struktur berorientasi objek, HTTP dan REST, SQL, Git, dan kebiasaan debugging. Rencana saya dua minggu untuk bahasanya — tipe, generik, LINQ, async dan await — dengan menulis program konsol kecil, bukan menonton video. Lalu dua minggu membangun satu API ASP.NET Core kecil dengan Entity Framework terhadap skema yang saya pahami, agar saya bertemu dependency injection dan migrasi dalam konteks. Setelah itu saya baca kode tim dan mengirim satu perubahan kecil yang ditinjau, serta meminta konvensi mereka di minggu pertama. |
| **Follow-up** | How would you know you were actually ready, rather than just finished with the tutorials? |
| **Weak answer / red flag** | "C# is like Java, I will pick it up in a few days"; or claiming .NET exposure from a course listing. |
| **Scoring anchor** | 1 = claims near-instant mastery · 3 = willing, generic plan · 5 = clean gap statement, precise transferable list, dated build-based plan, and a definition of ready |

---

### Q-FUND-20 — Complexity of a loop and a lookup

| Field | Value |
|---|---|
| **Category** | Programming Fundamentals |
| **Sub-skill** | Complexity |
| **Difficulty** | Advanced |
| **Asked in** | Technical |
| **Question (EN)** | You have a list of records and need to find matching ones. What is the cost of doing it with a loop, and how does a hash map change it? |
| **Pertanyaan (ID)** | Anda punya daftar catatan dan perlu menemukan yang cocok. Berapa biaya jika memakai perulangan, dan bagaimana hash map mengubahnya? |
| **What is assessed** | Whether you can reason about cost and choose a structure, not just recite Big-O notation. |
| **Evidence basis** | General knowledge; fact sheet §3.1 (attendance records and matching), §6.4 (SQL beyond SELECT). |
| **Strong answer outline** | • Nested loop: n × m comparisons, O(n·m) or O(n²) for equal sizes<br>• Hash lookup: average O(1), worst O(n) with collisions<br>• The trade: memory for time; build cost once, then cheap lookups<br>• Same idea as a database index; at scale, do it in SQL |
| **Model answer (EN)** | A loop that scans the second list for every item in the first is n times m comparisons, so quadratic when the lists are similar in size. Building a hash map keyed by the field I am matching on costs one pass, then each lookup is constant on average. So the whole job becomes linear, at the price of memory for the index. Two honest caveats: hashing is constant on average, not guaranteed — bad collisions degrade it towards linear — and if both sets live in a database, the right answer is usually a join with a proper index rather than pulling rows into memory and looping. |
| **Contoh jawaban (ID)** | Perulangan yang memindai daftar kedua untuk setiap item daftar pertama berarti n kali m perbandingan, sehingga kuadratik bila ukurannya mirip. Membangun hash map dengan kunci berupa field yang dicocokkan berbiaya satu lintasan, lalu setiap pencarian konstan secara rata-rata. Jadi keseluruhan pekerjaan menjadi linear, dengan harga memori untuk indeks. Dua catatan jujur: hashing konstan secara rata-rata, bukan jaminan — tabrakan buruk menurunkannya ke arah linear — dan kalau kedua kumpulan ada di basis data, jawaban yang tepat biasanya join dengan indeks yang benar, bukan menarik baris ke memori lalu mengulang. |
| **Follow-up** | Your hash map is built fresh on every request. What would you do about that? |
| **Weak answer / red flag** | "A loop is O(n)" stated for a nested loop; or claiming hash lookup is always O(1) with no caveat. |
| **Scoring anchor** | 1 = wrong complexity or no reasoning · 3 = correct notation, no trade-off · 5 = both costs, the memory trade, the average-versus-worst caveat, and the database-index parallel |
