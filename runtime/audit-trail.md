# Audit Trail Contract

The Audit Trail contract defines the minimum operational audit record used by
the NEOS runtime execution layer.

The v0.1.0 Audit Trail is documentary. It records governance-relevant runtime
actions and links them to authorization, decisions, evidence, incidents and
rollback.

## Purpose

Audit Trail preserves a reviewable path between:

- Authorization from Block 3.
- Task and event records from Block 4.
- Runtime observability events from Block 5.
- Decisions.
- Evidence.
- Incident records.
- Rollback notes.
- Runtime memory records.
- Context snapshots.

## Minimum audit entry

| Field | Requirement |
|---|---|
| `audit_id` | Required unique audit entry identifier. |
| `timestamp` | Required audit timestamp. |
| `runtime_component` | Runtime component responsible for the action. |
| `task_id` | Linked task identifier when applicable. |
| `event_id` | Linked Event Bus event identifier. |
| `action` | Audited action or governance-relevant event. |
| `authorization_ref` | Authorization reference from Block 3. |
| `decision_ref` | Decision log reference. |
| `evidence_ref` | Evidence log reference. |
| `incident_ref` | Incident log reference when applicable. |
| `rollback_ref` | Rollback reference when applicable. |
| `result` | Action result. |
| `risk_level` | Low, medium, high or critical runtime risk. |
| `notes` | Human-readable context. |

## Required log links

Audit entries must use stable references to:

- `logs/DECISION_LOG.md`
- `logs/EVIDENCE_LOG.md`
- `logs/EXECUTION_STATE_LOG.md`
- `logs/AUDIT_TRAIL.md`
- `logs/INCIDENT_LOG.md`
- `logs/MEMORY_LOG.md`
- `logs/CONTEXT_SNAPSHOT_LOG.md`

## Audit triggers

Create or link an audit entry when:

- A task is authorized.
- A state transition has runtime governance significance.
- Evidence is created for medium, high or critical work.
- An incident is opened, contained, resolved or closed.
- Rollback is requested, completed or fails.
- A runtime component is unavailable.
- Manual intervention is required.
- Persisted context is validated, deprecated, revoked or archived.
- Resume or recovery is approved, blocked or marked for review.
- A snapshot becomes the basis for a recovery decision.

## Rules

- Audit Trail records actions and outcomes; it does not authorize or execute.
- Audit entries must link decisions and evidence when available.
- Audit entries must link incidents when the action relates to a failure,
  blocked condition or manual intervention.
- Rollback-related audit entries must link rollback evidence.
- Missing audit entries for required runtime actions must be treated as an
  incident type `missing_audit_entry`.
- Memory affecting resume, recovery, rollback or incidents must link audit.
- Restricted, high or critical memory requires audit review before reuse.

## Non-goals

- No external audit system is implemented.
- No database or append-only ledger is introduced.
- No permission or secret management is changed.
