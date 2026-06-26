# Runtime Observability Contract

The Runtime Observability contract defines the minimum record used to observe,
classify and inspect NEOS runtime behavior.

The v0.1.0 observability layer is documentary. It records runtime facts and
links them to evidence, audit, incidents and rollback. It does not authorize,
execute, retry, rollback or mutate state by itself.

## Purpose

Runtime Observability makes execution reviewable across:

- Authorization outcomes.
- Task Queue records.
- Event Bus events.
- State Manager transitions.
- Evidence entries.
- Audit entries.
- Incident records.
- Rollback references.
- Runtime memory records.
- Context snapshots.

## Minimum observability event

| Field | Requirement |
|---|---|
| `observability_event_id` | Required unique observability event identifier. |
| `timestamp` | Required observation timestamp. |
| `runtime_component` | Component being observed. |
| `task_id` | Linked task identifier when applicable. |
| `event_type` | Runtime event taxonomy value or inspection category. |
| `state_before` | State before the observed event when applicable. |
| `state_after` | State after the observed event when applicable. |
| `severity` | Informational, warning, error or critical severity. |
| `risk_level` | Low, medium, high or critical runtime risk. |
| `evidence_ref` | Evidence log reference. |
| `audit_ref` | Audit trail reference. |
| `incident_ref` | Incident log reference when applicable. |
| `rollback_ref` | Rollback reference when applicable. |

## Severity values

| Severity | Meaning |
|---|---|
| `info` | Expected runtime event. |
| `warning` | Degraded or review-worthy condition. |
| `error` | Failed or blocked runtime condition. |
| `critical` | High-impact failure requiring immediate containment. |

## Rules

- Observability registers runtime facts for inspection.
- Observability must not execute actions by itself.
- Observability must not replace authorization, Event Bus or State Manager.
- Medium, high and critical observability events must link evidence.
- Failed, blocked, degraded or manual intervention events must link incidents.
- Rollback-related events must link rollback references and evidence.
- Memory reuse or context resume events must link memory records, snapshots,
  evidence and audit.
- Stale, deprecated or revoked context must be inspectable before it can block
  resume or recovery.

## Review fields

Runtime review may inspect observability by:

- `observability_event_id`
- `runtime_component`
- `task_id`
- `event_type`
- `state_before`
- `state_after`
- `severity`
- `risk_level`
- `evidence_ref`
- `audit_ref`
- `incident_ref`
- `rollback_ref`
- `context_id`
- `snapshot_id`

## Non-goals

- No monitoring vendor is introduced.
- No dashboard is implemented.
- No autonomous remediation is defined.
- No worker, queue transport or database is introduced.
