# Programming Fundamentals

**Purpose:** Give correct, short answers and survive the follow-up.
**Created / last updated:** 31 October 2026
**Evidence status:** General technical guidance, not claimed candidate experience.

## 1. Values, state and types

- A type describes valid values and operations. TypeScript checks types before execution; emitted JavaScript still needs runtime validation for external data.
- JavaScript assignments copy values. For an object, that value is a reference: two bindings may refer to one mutable object. Java and JavaScript are pass-by-value, including reference values; neither is general pass-by-reference.
- `const` prevents reassignment of a binding, not mutation of its object. A shallow copy shares nested references.
- `null` is explicit absence; `undefined` commonly indicates an unassigned/missing value in JavaScript. Validate both where the input contract permits them.
- Prefer exact decimal or integer minor units for money; binary floating-point cannot exactly represent many decimal fractions.

```ts
const original = { settings: { active: true } };
const shallow = { ...original };
shallow.settings.active = false; // also changes original.settings.active
const independent = { ...original, settings: { ...original.settings } };
```

**Drill:** What changes if the nested value is a string? Answer: strings are immutable primitive values; replacing one copied property does not mutate the other object.

## 2. OOP without slogans

| Concept | Meaning | Example |
|---|---|---|
| Encapsulation | Protect invariants through a controlled boundary | Stock cannot become negative through a public operation |
| Abstraction | Expose a useful contract, hide irrelevant implementation | `sendNotification()` hides provider details |
| Inheritance | Specialise an existing type | A subclass must honour the parent's contract |
| Polymorphism | Use one contract with different implementations | Email and SMS senders implement a notification contract |
| Composition | Build behaviour by combining collaborators | Order service receives a payment gateway |

An interface describes a contract. An abstract class can share state and implementation. Details differ: modern Java/C# interfaces can contain some implementations; TypeScript interfaces are erased and do not validate runtime objects. Prefer composition when behaviour varies independently. Inheritance is appropriate when substitutability is real, not merely to reuse two lines.

**SOLID, junior version:** one reason to change; add behaviour without repeatedly editing stable code; subtypes honour contracts; avoid giant interfaces; depend on contracts at useful boundaries. Do not create an interface for every trivial function.

## 3. Execution and failure

The call stack tracks function execution. Objects may live on managed heaps; actual placement is runtime/compiler dependent. C++ supports automatic lifetime and RAII as well as dynamic allocation. Garbage collection frees unreachable objects, not reachable-but-useless caches. Recursion consumes stack unless the environment optimises it.

JavaScript executes each job on a thread, while the host handles asynchronous I/O. Promise continuations use microtasks. `await` suspends the async function, not the entire server; a long synchronous loop still blocks that thread. Workers can run CPU work separately.

```ts
async function loadStudent(id: string) {
  const response = await fetch(`/api/students/${encodeURIComponent(id)}`);
  if (!response.ok) throw new Error(`Request failed: ${response.status}`);
  return response.json(); // validate shape before trusting it
}
```

Handle errors at a boundary that can do something useful. Add context without exposing secrets. Do not catch an error and silently report success. A timeout does not prove a write failed; retries need an idempotency strategy.

## 4. HTTP and APIs

| Method | Intended semantics | Safe? | Idempotent by semantics? |
|---|---|---|---|
| GET | Retrieve a representation | Yes | Yes |
| POST | Process a submitted representation | No | Not guaranteed |
| PUT | Replace/create resource at known URI | No | Yes |
| PATCH | Apply partial modification | No | Depends on operation |
| DELETE | Remove resource association | No | Yes |

Idempotency concerns intended effect, not identical response codes. Repeating DELETE may return 404 after 204 and remain idempotent. A POST can be implemented idempotently with a stored key and matching request payload.

Statuses: 200 success; 201 created; 202 accepted, not finished; 204 no body; 400 invalid request; 401 missing/invalid authentication credentials; 403 forbidden; 404 not found or deliberately concealed; 409 state conflict; 422 semantic validation failure; 429 rate limited; 500 unexpected server error; 503 temporarily unavailable.

REST is an architectural style with resources, representations and constraints including stateless requests. REST statelessness does not mean the database has no state. RPC describes operations such as `approveOrder`. Choose a clear contract rather than forcing every workflow into superficial CRUD.

## 5. Security boundaries

- Authentication establishes identity. Authorization checks permission on **this action and this object**. A hidden button is not access control.
- A session identifier normally points to server-side session state. A JWT carries signed claims; signatures do not encrypt the payload. Verify issuer, audience, expiry and algorithm. Revocation and rotation still need design.
- Cookies with `Secure`, `HttpOnly` and appropriate `SameSite` reduce specific risks; cookie-authenticated writes may require CSRF protection. JavaScript-readable tokens are exposed to XSS.
- CORS controls browser cross-origin access, not general API authorization. Non-browser clients do not obey it as an access policy.
- Passwords need salted, deliberately expensive password hashing such as Argon2id with appropriate parameters. Encryption is reversible with a key; hashes are not intended to be reversed.
- Validate input and use parameterised SQL. Authorize on the server; restrict database credentials; never put secrets in a frontend bundle.

## 6. Language bridges

| Family | Runtime/ecosystem | Transferable skill | Honest gap |
|---|---|---|---|
| PHP | Common server-side runtime; CodeIgniter | HTTP, validation, SQL | Framework/version details differ |
| JavaScript / TypeScript | Browser/Node; TS compiles to JS | Components, async I/O, typing | TS does not enforce runtime payload types |
| Java | JVM, static typing | OOP, SQL, service boundaries | No evidenced Java project |
| C# / .NET | Managed runtime, ASP.NET Core | OOP, async, APIs | No evidenced .NET project |
| AngularJS | Legacy JavaScript framework | UI/data separation | Not modern Angular |
| Angular | TypeScript framework | Component concepts | DI, change detection, RxJS require learning |
| Flutter / Dart | Cross-platform UI toolkit | UI composition, API calls | No evidenced Flutter app |

Ask whether the ad means AngularJS or modern Angular. They are not interchangeable. Do not promise a fixed time to production competence.

## 7. Twelve oral checks

1. **TypeScript vs JavaScript?** TS adds static checking; it emits JS. Validate untrusted input at runtime.
2. **Interface vs abstract class?** Contract versus shared implementation/state, with language-specific exceptions.
3. **Why composition?** Swap behaviour without fragile subtype assumptions; extra indirection is a cost.
4. **Why immutable state?** Easier reasoning and change detection; copying can cost time/memory.
5. **What does `await` block?** The async function's continuation, not the host's entire event loop.
6. **401 vs 403?** Invalid/missing credentials versus refusal; 403 does not universally guarantee authentication occurred.
7. **PUT vs PATCH?** Replacement versus partial change; PATCH is not automatically idempotent.
8. **JWT vs session?** Token claims versus lookup-based state; both require secure lifecycle management.
9. **Hash vs encryption?** Verification without recovery versus reversible confidentiality.
10. **Why parameterised SQL?** Keep data separate from query structure; still validate business rules.
11. **What is a memory leak under GC?** Retaining reachable objects that the application no longer needs.
12. **Unknown stack?** State the gap, explain a transferable concept, propose a small reviewed learning task.

**Resources (recommended, not newly retrieved):** MDN https://developer.mozilla.org/en-US/docs/Web/JavaScript ; HTTP https://developer.mozilla.org/en-US/docs/Web/HTTP ; TypeScript https://www.typescriptlang.org/docs/ ; OWASP https://cheatsheetseries.owasp.org/ . Resource list compiled 31 Oct 2026; no fresh retrieval claimed.
