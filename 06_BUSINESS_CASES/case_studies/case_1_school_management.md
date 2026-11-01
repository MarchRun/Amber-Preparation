# Case 1 — School Management

**Purpose:** Work through attendance, grading and permissions.
**Created:** 31 October 2026
**Last updated:** 1 November 2026 — canonical case-study location.
**Status:** Fictional practice scenario. Not an Amber client, project, or brief.

## 1. Candidate brief — stop before the solution

A private school operates three campuses. Staff record attendance manually and prepare report cards in spreadsheets. Parents receive inconsistent information. Propose a first release that improves attendance and term reports. Budget and exact user counts are not given. Take 45 minutes and produce one page plus a five-minute explanation.

Deliver: clarifying questions, MVP, architecture, entities, two key APIs, integrity/security rules, trade-off, risks and pilot acceptance tests. Do not assume an admissions, tuition or payroll system is requested.

---

## 2. Worked solution: clarify and scope

Ask: Is attendance per day or teaching session? Are all campuses governed by the same grading rules? Who approves corrections and report cards? Must the first release integrate existing student IDs? Which guardian relationships permit access? Is connectivity reliable? What is the lawful retention/consent process for children's data?

**Exercise assumptions:** attendance is per scheduled session; campuses share a term calendar but subjects can have different approved weightings; teachers can submit corrections, administrators can approve locked-term changes; guardians see only linked children. These are proposed assumptions, not known institutional policy.

MVP: import roster, enroll students in classes, schedule sessions, capture attendance, correct with audit, enter grades and produce approved term reports. Later: RFID automation, messaging and offline capture. Exclude admissions, fees, payroll and full learning-management content.

Success: pilot staff can reconcile one week's records against the schedule, explain every correction and generate one approved report with no cross-child access. Numerical success targets must be agreed with the school, not fabricated here.

## 3. Design

```text
Teacher / admin / guardian browser
              | HTTPS + authenticated session
       Modular application
         | roster | attendance | grades | reports
              | transactions / object authorization
         PostgreSQL + restricted audit
              |
       optional export worker -> private object storage
```

One application avoids distributed consistency overhead. Choose a stack the delivery team can support, not simply the newest framework. Marchel can discuss a TypeScript/PostgreSQL proposal or PHP alternative without claiming this design is his actual project.

| Entity | Keys and relationships |
|---|---|
| campus | campus_id |
| student | student_id, institutional identifier, status |
| guardian_link | guardian_user_id + student_id; verified authority |
| class / enrollment | class belongs to campus; student enrolled for term |
| session | class_id, start/end timestamp, timezone context |
| attendance | student_id + session_id unique; status, provenance |
| assessment | subject/class/term, maximum score and approved weighting |
| grade | student_id + assessment_id unique; score and revision |
| report_release | term/student, version, approver, released_at |
| audit_event | actor, action, target, reason, old/new reference, time |

Enrollment dates matter: do not mark a student absent before they joined. A missing record remains "not recorded" until policy determines absence. Reports must separate missing data from explicit absent/leave/present states.

## 4. Rules and API

| Endpoint | Behaviour and checks |
|---|---|
| `POST /sessions/{id}/attendance` | Assigned teacher, active enrollment, open period, duplicate-safe write |
| `PATCH /attendance/{id}` | Authorized actor; reason and expected version; audited correction |
| `PUT /assessments/{id}/grades/{studentId}` | Score bounds; teacher assignment; reject locked period |
| `GET /students/{id}/term-reports/{term}` | Student/guardian link or authorized staff; released version only |
| `POST /term-reports/{id}/release` | Approver only; completeness checks; immutable released version |

Attendance rate = present scheduled eligible sessions / eligible scheduled sessions, subject to explicit leave/cancel rules. Report the denominator. Grade = sum(normalised score × approved weight). Weights must total 100% for a completed grading plan; handle missing/withdrawn assessments by policy, not silently as zero. Store precise values and round once at the reporting boundary using the agreed rule.

RFID extension: authenticate gateway; map active card to student; deduplicate device event IDs; choose valid session; acknowledge after durable handling. A scan is evidence of a card event, not proof of identity or full-day presence. Preserve manual correction with audit.

## 5. Security and privacy

Teacher permissions are assignment-scoped; admin permissions may also be campus-scoped. A guardian link must be verified and revocable. Enforce checks in APIs and export downloads, not only navigation. Use least privilege, TLS, managed authentication, limited exports and auditable access. Do not store unnecessary personal data in device logs. Agree retention, deletion and legal obligations with responsible school/legal staff; this is not a legal opinion. Use synthetic data for development.

## 6. Alternatives and failure paths

| Decision | Choice | Cost / revisit condition |
|---|---|---|
| Build vs configure existing school package | Evaluate package fit first | Custom rules may justify development only after gap analysis |
| RFID vs QR/manual | Manual/QR pilot before hardware expansion | QR can be shared; RFID requires devices/cards and still has misuse risks |
| Live vs scheduled reports | Generate from consistent released snapshot | Not every edit appears until next approval |

Offline teacher: record a local pending action with stable ID; never show it as synced before confirmation. Closed-term late event: quarantine for approval. Concurrent correction: version check returns conflict rather than losing changes. Wrong guardian mapping: revoke immediately and audit access.

## 7. Tests and delivery

Unit: rounding, weights, eligible-session calculation, timezone boundary. Integration: unique attendance, enrollment dates, report lock, audit transaction. E2E: teacher records, admin corrects, guardian sees only their child's released report. Security: guessed student ID, expired link, unauthorized CSV download. Recovery: restore backup and reconcile a sample period.

Pilot sequence: agree workflows/roles → import sample roster with validation → capture one class's attendance → run parallel reconciliation → add grade workflow → review guardian access → expand campus by campus. Dates and staffing are estimates to confirm, not delivery promises.

## 8. Five-minute walkthrough cue script

"I would first confirm whether attendance is daily or per session and who approves report cards. My proposed MVP covers roster, scheduled attendance and approved term reports, not fees or admissions.

I recommend one modular application with a relational database. The key relationships are enrollment, session, attendance, assessment and grade. Attendance is unique per student and session. Eligible enrollment and cancelled sessions determine the denominator, so missing data is not automatically counted as absence.

Teachers can change only assigned classes. Guardians see only verified linked children. Corrections keep actor, reason and history, and released reports have versions. Grade weights and rounding rules are agreed with the school.

I would pilot with manual or QR capture while evaluating hardware and existing packages. RFID could be added through authenticated, duplicate-safe device events, but it does not eliminate correction or identity risks.

The important tests are duplicate scans, unassigned teachers, wrong guardian links and reports with missing grades. I would begin with one class, reconcile records in parallel, validate the released report and only then expand. My next question is which existing system owns the student roster."

Expand these cues with the diagram and one correction example to fill five minutes; do not race through every entity. Transferable candidate evidence: SMB Suvanna Dipa web roles and RFID integration only. The three-campus scenario, grading design and privacy processes above are fictional proposals.
