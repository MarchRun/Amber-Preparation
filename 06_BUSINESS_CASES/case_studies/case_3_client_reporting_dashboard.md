# Case 3 — Multi-Client Reporting Dashboard

**Purpose:** Define trusted metrics, freshness and tenant boundaries.
**Created:** 31 October 2026
**Last updated:** 1 November 2026 — canonical case-study location.
**Status:** Fictional practice scenario. Not an Amber client, project, or brief.

## 1. Candidate brief

A consultancy consolidates client reports from three source systems. Staff manually combine spreadsheets; clients dispute inconsistent totals. Propose a multi-client dashboard. The source interfaces, KPI definitions and required refresh rate have not been supplied. Take 45 minutes; do not assume real-time data is necessary.

## 2. Clarify and set scope

Which decision does each report support? Who defines each KPI? Which source owns each field? What are the currency, timezone and period-close rules? Can records change retrospectively? Is each client a separate tenant? Who can export or view aggregated cross-client data? Are APIs available, and what rate limits apply?

Assume daily refresh is sufficient for the pilot, sources permit read-only export/API access, and clients see only their own data. Treat those as testable assumptions. MVP: two agreed KPIs, source-to-report traceability, freshness/quality indicators, scoped dashboard and export. Defer predictive analytics and ad-hoc cross-client queries.

## 3. Architecture and model

```text
Source A API   Source B export   Source C API
       \            |            /
       read-only ingestion adapters
                    |
         raw input + run metadata
                    |
         validation / mapping / dedupe
                    |
         tenant-scoped reporting snapshot
                    |
             API -> dashboard / private export
```

Use a scheduled job and database first. A data lake, stream platform and multiple services are optional only when actual volume, governance or latency justify them.

| Entity | Important fields |
|---|---|
| tenant / membership | tenant ID, user, role, active period |
| source_config | tenant, source type, secret reference, watermark |
| ingestion_run | started/finished time, status, row counts, checksum |
| raw_record | tenant, source ID/version, received time, payload reference |
| mapping_rule | source field to canonical field, rule version |
| metric_definition | owner, formula, unit, period, exclusions, version |
| report_snapshot | tenant, as_of, source watermarks, quality status |
| exception | run, record reference, reason, owner, resolution |

Keys must include source/tenant context where identifiers overlap. Store credentials in secret management. Raw data requires restricted access and a retention policy; preserving it forever is not a default.

## 4. Workflow and API

1. Start a run with a stable run ID and previous watermark.
2. Fetch bounded pages with rate-limit-aware retries.
3. Store input and provenance; validate IDs, types, currency, dates and mandatory fields.
4. Deduplicate by stable source record/version or documented business key.
5. Apply versioned mappings and metric definitions.
6. Compare source control totals and counts; quarantine exceptions.
7. Publish a complete snapshot atomically. Advance watermark only after successful durable processing.
8. Expose freshness and partial-data status, not misleading zero totals.

Allow a lookback/reconciliation window for late changes; a simple maximum-timestamp watermark can miss out-of-order updates. Define deletes and corrections, not only new records.

Endpoints: `GET /reports?period=...`, `GET /reports/{id}/provenance`, `GET /ingestion-runs/{id}`, `POST /exports`, `GET /exports/{id}`. Authenticate, verify tenant membership and authorize each object. Derive scope from verified access, not only an arbitrary tenant parameter. Add tenant scope to cache keys and export paths; recheck access on download.

Example KPI definition: "Net posted sales in original currency for the business-local period, excluding cancelled documents and including approved returns by their posting date." A real owner must confirm this; never silently sum currencies or mix order and posting dates.

## 5. Decisions and failures

| Option | Choose for pilot | Cost / revisit trigger |
|---|---|---|
| Batch vs streaming | Scheduled batch | Daily latency; revisit if same-hour decisions matter |
| Direct source query vs reporting store | Reporting store | Extra copy/refresh logic, but isolates operational systems |
| Latest partial data vs complete snapshot | Complete snapshot with freshness warning | Older data during one-source outage |
| Row-level security vs application-only filters | Defense in depth if supported and operated correctly | Requires correct tenant/session context and testing |

If one source fails, retain the last complete snapshot and show its age. If definition changes, version it and explain whether prior periods are recomputed. If source schema changes, fail validation rather than assigning fields by spreadsheet position and silently corrupting totals. If credentials expire, alert the responsible owner without logging secrets.

## 6. Test and delivery plan

Unit: metric formula, currency policy, period boundaries, mapping versions. Integration: pagination retry, duplicate ingestion, late update/delete, source totals, atomic snapshot publish. Security: same resource ID across tenants, revoked membership, export URL guessing, cache scope. E2E: client sees a report, freshness label and traceable exception status.

Rollout: agree KPI dictionary and owners → obtain synthetic/sample extracts → reconcile one tenant and one period → implement repeatable ingest → parallel-run against accepted manual report → release read-only pilot → expand sources/tenants. A beautiful dashboard is not accepted until the figures agree for the right reasons.

## 7. Five-minute presentation cues

"I would begin with definitions, not charts. The discrepancy could be a date, currency or cancellation rule rather than a coding error. I would ask for a KPI owner and the required freshness.

My pilot uses daily ingestion from three read-only adapters into restricted raw input and a validated reporting snapshot. Source IDs, mapping versions and run metadata make each total traceable. Failed validation creates an exception, not a silent zero.

Every query, cache and export is tenant-scoped. A tenant field in a request is not proof of permission. I would test two tenants with overlapping record IDs.

I choose scheduled batch over streaming because real-time demand is not given. The cost is latency; the benefit is simpler operation and reconciliation. During an outage the dashboard shows the last complete snapshot and its age.

The first deliverable is one reconciled tenant report with agreed formulas. Once the client accepts that, I would expand the sources and periods. The next question is which system is authoritative when totals disagree."

Use remaining speaking time to show one metric calculation and one late-arrival example. None of this is claimed as inside knowledge about Amber or FOOMA implementation.
