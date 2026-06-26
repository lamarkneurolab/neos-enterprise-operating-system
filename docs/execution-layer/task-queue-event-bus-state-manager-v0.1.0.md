# Task Queue, Event Bus & State Manager v0.1.0

This is the canonical specification for NEOS Block 4.

Block 4 defines the minimum runtime coordination layer for task registration,
event traceability, state governance, rollback hooks and audit linkage.

## Purpose

The purpose of this block is to make runtime execution traceable before,
during and after work is performed.

The layer ensures that authorized tasks have a durable contract for:

- Task identity.
- Authorization and execution status.
- Event emission.
- State transition control.
- Evidence linkage.
- Audit linkage.
- Rollback evaluation.

## Scope

Included:

- Task Queue contract.
- Event Bus contract.
- State Manager contract.
- Execution State Log.
- Rollback hooks.
- Audit linkage.
- Required lifecycle.
- Valid and blocked transitions.
- Minimum task, event and state transition records.

## Non-goals

Excluded:

- Business agents.
- Production workers.
- Autonomous execution.
- Kafka, RabbitMQ, Redis or database implementation.
- External service integration.
- Permission changes.
- Automatic merge.

## Runtime placement

The Runtime Coordination Layer receives work only after the Authorization Flow
produces an `Authorized` outcome.

```text
Authorization Flow
  -> Task Queue
  -> Event Bus
  -> State Manager
  -> Runtime Observability
  -> Audit Trail / Incident Records
  -> Execution State Log
  -> Evidence / Audit / Rollback
```

The layer does not replace authorization. It records authorized work, emits
events, validates state transitions and preserves auditability.

Block 5 adds Runtime Observability and Audit Trail after the Block 4
coordination layer. This does not replace the Task Queue, Event Bus or State
Manager. It adds inspection, health, incident and audit records that link back
to Block 4 task, event and state records.

## Task Queue

The Task Queue is the runtime task record contract. It records execution
candidates and their governance references.

The v0.1.0 Task Queue is not a production queue, worker pool or external
storage system.

Required rules:

- No task may move to `in_progress` without valid authorization.
- Every task must have a `task_id`.
- Every task that modifies repository or external systems must evaluate
  rollback.
- Medium, high and critical tasks must link evidence.
- Failed tasks must emit `task.failed`.
- Completed tasks must emit `task.completed`.

## Event Bus

The Event Bus is the internal runtime event contract. It records state changes,
evidence creation and audit-relevant events.

The v0.1.0 Event Bus is a traceability contract, not an autonomous execution
engine.

Required rules:

- Every state transition must emit an event.
- Every event must link back to a `task_id` unless it is a system-level audit
  event.
- Critical events must link evidence or audit.
- Block 5 inspection may query events by event identity, task identity,
  component, severity, timestamp, state transition, audit, evidence and incident
  references.

## State Manager

The State Manager governs task state transitions. It defines allowed next
states, blocked transitions, authorization requirements, evidence requirements
and rollback conditions.

Required rules:

- Runtime must not skip states.
- Every state transition must be logged.
- Invalid transitions must be blocked.
- Rollback states require evidence before closure.

## Execution State Log

The Execution State Log records state transitions for human review.

The canonical log is `logs/EXECUTION_STATE_LOG.md`.

Each state log row must include:

- Date.
- State Log ID.
- Task ID.
- Event ID.
- Previous State.
- Next State.
- Reason.
- Actor.
- Evidence.
- Rollback.

## Rollback Hooks

Rollback hooks document whether rollback is required and how rollback closure
is evidenced.

Required rollback hooks:

- Tasks that modify repository or external systems must set
  `rollback_required` to `true`, `false` or `not_required`.
- Failed tasks that need remediation must transition to `rollback_requested`.
- Rollback completion must emit `task.rollback.completed`.
- Rollback closure must link evidence.

## Audit Linkage

Audit linkage connects runtime coordination records to governance evidence.

Required links:

- `linked_decision` connects the task to `logs/DECISION_LOG.md`.
- `linked_evidence` connects the task or event to `logs/EVIDENCE_LOG.md`.
- `audit_reference` connects events to audit records when required.
- `evidence_reference` is required for medium, high and critical work.
- `incident_reference` connects failed, blocked, degraded or manual
  intervention conditions to `logs/INCIDENT_LOG.md`.

## Block 5 observability linkage

Runtime Observability and Audit Trail extend Block 4 with review records:

| Block 5 record | Required Block 4 link |
|---|---|
| Observability event | `task_id`, `event_id`, state before and state after when applicable. |
| Audit entry | `task_id`, `event_id`, authorization, decision and evidence references. |
| Health signal | Runtime component and linked task when applicable. |
| Incident record | `task_id`, `event_id`, evidence, audit and rollback references. |

Observability records, classifies and inspects. It must not execute actions or
change task state by itself.

## Required lifecycle

```text
queued
  -> authorized
  -> in_progress
  -> completed
```

Blocking lifecycle:

```text
queued
  -> blocked
  -> cancelled
```

Failure and rollback lifecycle:

```text
in_progress
  -> failed
  -> rollback_requested
  -> rolled_back
```

If rollback fails, the task may remain or return to `failed` with evidence.

## Valid transitions

| Previous state | Next state |
|---|---|
| queued | authorized |
| queued | blocked |
| authorized | in_progress |
| authorized | cancelled |
| blocked | cancelled |
| in_progress | completed |
| in_progress | failed |
| failed | rollback_requested |
| rollback_requested | rolled_back |
| rollback_requested | failed |

## Blocked transitions

| Previous state | Blocked next state | Reason |
|---|---|---|
| queued | in_progress | Authorization must be recorded first. |
| queued | completed | Runtime must not skip execution states. |
| blocked | in_progress | Blocked tasks cannot execute. |
| failed | completed | Failed tasks require rollback or remediation. |
| completed | in_progress | Completed tasks are closed. |
| cancelled | in_progress | Cancelled tasks cannot restart without a new task. |
| rolled_back | completed | Rolled back tasks close as rollback records. |

## Event taxonomy

| Event type | Purpose |
|---|---|
| `task.created` | A task record was created. |
| `task.authorized` | Authorization was recorded for the task. |
| `task.blocked` | The task was blocked before execution. |
| `task.started` | The task entered `in_progress`. |
| `task.completed` | The task completed successfully. |
| `task.failed` | The task failed. |
| `task.cancelled` | The task was cancelled. |
| `task.rollback.requested` | Rollback was requested. |
| `task.rollback.completed` | Rollback was completed. |
| `state.transitioned` | A state transition was recorded. |
| `evidence.created` | Evidence was created or linked. |
| `audit.logged` | Audit information was recorded. |

## Minimum task record

| Field | Requirement |
|---|---|
| `task_id` | Unique task identifier. |
| `task_type` | Work category or intent class. |
| `task_source` | Originating request, plan or system. |
| `requested_by` | Human or runtime actor requesting work. |
| `authorization_status` | Authorization outcome. |
| `execution_status` | Current execution state. |
| `risk_level` | Low, medium, high or critical. |
| `priority` | Execution priority. |
| `created_at` | Task creation timestamp. |
| `updated_at` | Last update timestamp. |
| `assigned_runtime` | Runtime responsible for execution. |
| `linked_capabilities` | Capability registry references. |
| `linked_permissions` | Permission registry references. |
| `linked_decision` | Decision log reference. |
| `linked_evidence` | Evidence log reference. |
| `rollback_required` | Rollback requirement. |

## Minimum event record

| Field | Requirement |
|---|---|
| `event_id` | Unique event identifier. |
| `event_type` | Event taxonomy value. |
| `timestamp` | Event timestamp. |
| `source_component` | Component emitting the event. |
| `task_id` | Linked task, except system-level audit events. |
| `previous_state` | State before transition when applicable. |
| `next_state` | State after transition when applicable. |
| `actor` | Human or runtime actor. |
| `authorization_reference` | Authorization record. |
| `decision_reference` | Decision log reference. |
| `evidence_reference` | Evidence log reference. |
| `audit_reference` | Audit log reference. |
| `payload_summary` | Human-readable event summary. |

## Minimum state transition record

| Field | Requirement |
|---|---|
| `state_id` | Unique state record identifier. |
| `task_id` | Linked task identifier. |
| `current_state` | Current task state. |
| `allowed_next_states` | Permitted next states. |
| `blocked_transitions` | Prohibited transitions. |
| `required_authorization` | Authorization needed for transition. |
| `required_evidence` | Evidence needed for transition or closure. |
| `rollback_condition` | Condition that triggers rollback. |
| `failure_condition` | Condition that marks failure. |

## Verification

Minimum verification for this documentation block:

```text
git status -sb
git diff --check
git diff --stat
git log --oneline --decorate -n 5
```

If `markdownlint` is available, run:

```text
markdownlint "**/*.md"
```

## Acceptance criteria

Block 4 v0.1.0 is complete when:

1. Required Block 4 files are created.
2. Required existing files are updated.
3. Task Queue contract is documented.
4. Event Bus contract is documented.
5. State Manager contract is documented.
6. Valid transitions are documented.
7. Blocked transitions are documented.
8. Rollback hooks are documented.
9. Audit linkage is documented.
10. No business agents are created.
11. No production workers are introduced.
12. No external service implementation is introduced.
13. Validation commands are executed.
14. A non-empty commit is created.
15. A Draft PR is opened for human review.
16. No automatic merge is performed.
