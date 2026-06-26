# Health Signals Contract

The Health Signals contract defines the minimum runtime readiness and integrity
signals used for NEOS runtime review.

The v0.1.0 Health Signals layer is documentary. It does not implement active
monitoring, alerting, dashboards or external probes.

## Purpose

Health Signals make runtime availability and traceability visible before,
during and after execution.

## Minimum signals

| Signal | Meaning |
|---|---|
| `runtime.available` | Runtime documentation and execution context are available. |
| `queue.accepting_tasks` | Task Queue contract can accept authorized task records. |
| `event_bus.accepting_events` | Event Bus contract can accept event records. |
| `state_manager.validating_transitions` | State Manager can validate transitions. |
| `audit_trail.writable` | Audit Trail can record entries. |
| `evidence_log.available` | Evidence Log can record or reference evidence. |
| `incident_log.available` | Incident Log can record incidents. |
| `rollback_hooks.available` | Rollback hooks can be evaluated and referenced. |

## Minimum statuses

| Status | Meaning |
|---|---|
| `healthy` | Component is available and expected to support execution. |
| `degraded` | Component is available but has a review-worthy limitation. |
| `blocked` | Component cannot safely support execution. |
| `failed` | Component failed during runtime activity. |
| `unknown` | Component status has not been verified. |

## Minimum health record

| Field | Requirement |
|---|---|
| `health_signal_id` | Unique health signal record identifier. |
| `timestamp` | Signal observation timestamp. |
| `signal` | One of the required signal names. |
| `status` | One of the minimum statuses. |
| `runtime_component` | Component represented by the signal. |
| `task_id` | Linked task when applicable. |
| `evidence_ref` | Evidence log reference when applicable. |
| `audit_ref` | Audit trail reference when applicable. |
| `incident_ref` | Incident log reference when degraded, blocked or failed. |
| `notes` | Human-readable context. |

## Rules

- `blocked`, `failed` and unresolved `degraded` signals must be reviewed before
  closing an execution.
- Health signals that block execution must link an incident record.
- Health signals that affect rollback must link rollback evidence.
- Health Signals do not execute remediation by themselves.

## Non-goals

- No uptime service is introduced.
- No external monitoring vendor is introduced.
- No automatic alerting is implemented.
