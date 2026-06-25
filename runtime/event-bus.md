# Event Bus Contract

The Event Bus contract defines the minimum internal event record used by the
NEOS Runtime Coordination Layer.

The v0.1.0 Event Bus is a traceability contract, not an autonomous execution
engine or production event transport.

## Purpose

The Event Bus records runtime events so tasks, state changes, evidence, audit
and rollback remain linked for human review.

## Minimum event taxonomy

| Event type | Meaning |
|---|---|
| `task.created` | A task record was created. |
| `task.authorized` | The task was authorized. |
| `task.blocked` | The task was blocked. |
| `task.started` | The task entered `in_progress`. |
| `task.completed` | The task completed. |
| `task.failed` | The task failed. |
| `task.cancelled` | The task was cancelled. |
| `task.rollback.requested` | Rollback was requested. |
| `task.rollback.completed` | Rollback completed. |
| `state.transitioned` | A task state changed. |
| `evidence.created` | Evidence was created or linked. |
| `audit.logged` | Audit information was recorded. |

## Minimum event record

| Field | Requirement |
|---|---|
| `event_id` | Required unique event identifier. |
| `event_type` | Event taxonomy value. |
| `timestamp` | Event creation timestamp. |
| `source_component` | Component that emitted the event. |
| `task_id` | Linked task, except system-level audit events. |
| `previous_state` | Previous task state when applicable. |
| `next_state` | Next task state when applicable. |
| `actor` | Human or runtime actor. |
| `authorization_reference` | Authorization outcome or record. |
| `decision_reference` | Decision log reference. |
| `evidence_reference` | Evidence log reference. |
| `audit_reference` | Audit log reference. |
| `payload_summary` | Human-readable event summary. |

## Rules

- Every state transition must emit an event.
- Every event must link back to a `task_id` unless it is a system-level audit
  event.
- Critical events must link evidence or audit.
- Failed tasks must emit `task.failed`.
- Completed tasks must emit `task.completed`.
- Rollback requests must emit `task.rollback.requested`.
- Completed rollback must emit `task.rollback.completed`.

## Critical events

Critical events include:

- High or critical risk task transitions.
- Repository modifications.
- External side-effect requests.
- Failure states.
- Rollback request and rollback completion states.
- Audit registration events.

Critical events must link at least one of:

- `evidence_reference`
- `audit_reference`

## Non-goals

- No event broker is implemented.
- No Kafka, Redis, RabbitMQ or database is introduced.
- No autonomous retry, scheduling or worker execution is defined.
