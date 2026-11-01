# Data Model and API Examples

**Purpose:** Reusable patterns for fictional practice designs.
**Created:** 31 October 2026
**Last updated:** 1 November 2026 — canonical database-design location.
**Status:** PostgreSQL examples, reasoned review only; not executed in this session.

## 1. Naming and invariants

Use consistent singular/plural names, stable IDs, explicit units and timezone-aware timestamps. Foreign keys protect references; CHECK protects row values; unique keys protect business uniqueness. Cross-row/cross-table invariants often need transactions or other appropriate enforcement. Audit fields are not an audit history by themselves.

Eight snippets form one small example when run in order in an empty schema:

```sql
-- 1: tenant
CREATE TABLE tenant (id bigint PRIMARY KEY, name text NOT NULL);
```
```sql
-- 2: identity, independent of tenant membership
CREATE TABLE app_user (
 id bigint PRIMARY KEY, auth_subject text NOT NULL UNIQUE,
 created_at timestamptz NOT NULL DEFAULT now()
);
```
```sql
-- 3: role membership (RBAC)
CREATE TABLE membership (
 tenant_id bigint REFERENCES tenant(id), user_id bigint REFERENCES app_user(id),
 role text NOT NULL CHECK (role IN ('admin','mentor','viewer')),
 PRIMARY KEY (tenant_id,user_id)
);
```
```sql
-- 4: tenant-scoped student, including lifecycle metadata
CREATE TABLE student (
 tenant_id bigint REFERENCES tenant(id), id bigint NOT NULL, name text NOT NULL,
 created_at timestamptz NOT NULL DEFAULT now(), deleted_at timestamptz,
 PRIMARY KEY (tenant_id,id)
);
```
```sql
-- 5: session
CREATE TABLE class_session (
 tenant_id bigint REFERENCES tenant(id), id bigint NOT NULL,
 starts_at timestamptz NOT NULL, ends_at timestamptz NOT NULL,
 CHECK (ends_at > starts_at), PRIMARY KEY (tenant_id,id)
);
```
```sql
-- 6: attendance with tenant-consistent foreign keys
CREATE TABLE attendance_record (
 tenant_id bigint NOT NULL, student_id bigint NOT NULL, session_id bigint NOT NULL,
 status text NOT NULL CHECK (status IN ('present','absent','leave')),
 version integer NOT NULL DEFAULT 1 CHECK (version > 0),
 PRIMARY KEY (tenant_id,student_id,session_id),
 FOREIGN KEY (tenant_id,student_id) REFERENCES student(tenant_id,id),
 FOREIGN KEY (tenant_id,session_id) REFERENCES class_session(tenant_id,id)
);
```
```sql
-- 7: retry deduplication; same key + different hash must be rejected by handler
CREATE TABLE request_key (
 tenant_id bigint REFERENCES tenant(id), key text NOT NULL, request_hash text NOT NULL,
 state text NOT NULL CHECK (state IN ('pending','complete')),
 response_body jsonb, expires_at timestamptz NOT NULL,
 PRIMARY KEY (tenant_id,key)
);
```
```sql
-- 8: restricted audit history (enforce append-only write policy separately)
CREATE TABLE audit_event (
 id bigint GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
 tenant_id bigint NOT NULL REFERENCES tenant(id), actor_id bigint REFERENCES app_user(id),
 action text NOT NULL, target text NOT NULL, reason text,
 occurred_at timestamptz NOT NULL DEFAULT now()
);
```

These snippets do not implement full authentication, enrollment checks, privacy policy or row-level security. Do not mistake a schema for a complete secure application. Soft deletion requires queries to filter appropriately and an agreed retention/erasure process.

## 2. API conventions

`GET /students?limit=25&after=...` returns a bounded page with a stable cursor. `POST /attendance-records` creates or records a domain action. `PATCH /attendance-records/{id}` changes a record with an expected version and correction reason. Reject unknown fields or explicitly define extensibility; validate payload types and limits.

Success: 200/201/204 as appropriate. Validation: 400/422; missing credentials: 401; denied operation: 403 or concealed 404; version conflict: 409; rate limit: 429. Do not return 200 with an undocumented error object.

```json
{
  "error": {
    "code": "VERSION_CONFLICT",
    "message": "This record changed. Refresh before retrying.",
    "request_id": "example-request-id"
  }
}
```

Idempotency records must be claimed atomically, scoped to actor/tenant/operation as appropriate, and committed consistently with the action. Store/compare a request hash, return original result for a completed duplicate and define pending/concurrent behaviour. A key header alone does nothing.

Use explicit API versioning when a breaking contract requires it; additive compatible changes may not require a new version. Document auth, examples, errors and pagination. Never place credentials or personal secrets in URLs.

## 3. OpenAPI-style contract excerpt

```yaml
openapi: 3.0.3
info: {title: Practice Attendance API, version: 1.0.0}
paths:
  /attendance-records:
    post:
      summary: Record attendance in the caller's authorized scope
      parameters:
        - in: header
          name: Idempotency-Key
          required: true
          schema: {type: string, minLength: 1, maxLength: 128}
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              additionalProperties: false
              required: [student_id, session_id, status]
              properties:
                student_id: {type: integer, format: int64}
                session_id: {type: integer, format: int64}
                status: {type: string, enum: [present, absent, leave]}
      responses:
        '201': {description: Recorded}
        '401': {description: Missing or invalid credentials}
        '403': {description: Operation not permitted}
        '409': {description: Conflicting state or idempotency payload}
        '422': {description: Invalid attendance input}
```

Excerpt only: a deployable contract must define security schemes and response bodies. Tenant scope comes from verified authorization, not an unchecked client field.
