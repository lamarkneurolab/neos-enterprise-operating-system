# Task Queue Contract

The Task Queue contract defines the minimum task record used by the NEOS
Runtime Coordination Layer.

The v0.1.0 Task Queue is documentation and traceability infrastructure. It is
not a production worker queue, scheduler, database or external service.

## Purpose

The Task Queue records tasks that have entered runtime coordination. It keeps
the link between authorization, execution status, evidence, audit and rollback.

## Minimum task record

| Field | Requirement |
|---|---|
| `task_id` | Required unique task identifier. |
| `task_type` | Task category or intent class. |
| `task_source` | User request, approved plan or system source. |
| `requested_by` | Human or runtime actor requesting the task. |
| `authorization_status` | Authorized, blocked, rejected or pending. |
| `execution_status` | Current task execution state. |
| `risk_level` | Low, medium, high or critical. |
| `priority` | Task priority for coordination. |
| `created_at` | Creation timestamp. |
| `updated_at` | Last update timestamp. |
| `assigned_runtime` | Runtime expected to handle the task. |
| `linked_capabilities` | Capability registry references. |
| `linked_permissions` | Permission registry references. |
| `linked_decision` | Decision log reference. |
| `linked_evidence` | Evidence log reference. |
| `rollback_required` | Rollback requirement or `not_required`. |

## Minimum execution states

| State | Meaning |
|---|---|
| `queued` | Task is registered and awaiting authorization outcome. |
| `authorized` | Task has valid authorization to proceed. |
| `blocked` | Task cannot proceed under current conditions. |
| `in_progress` | Task execution has started. |
| `completed` | Task completed and emitted completion evidence. |
| `failed` | Task failed and emitted failure evidence. |
| `rollback_requested` | Rollback or remediation has been requested. |
| `rolled_back` | Rollback has completed with evidence. |
| `cancelled` | Task was cancelled before completion. |

## Rules

- No task may move to `in_progress` without valid authorization.
- Every task must have a `task_id`.
- Every task that modifies repository or external systems must evaluate
  rollback.
- Medium, high and critical tasks must link evidence.
- Failed tasks must emit `task.failed`.
- Completed tasks must emit `task.completed`.
- SDK and integration contract work must be represented as a task when it
  changes runtime state, compatibility, evidence, audit or rollback posture.

## Traceability

Every task should preserve links to:

- Authorization outcome.
- Capability registry entry.
- Permission registry entry.
- Decision log entry.
- Evidence log entry.
- State transition records.
- Rollback status.
- SDK or integration contract reference when applicable.

## Non-goals

- No business agents are created.
- No production workers are implemented.
- No Kafka, Redis, RabbitMQ or database is introduced.
- No external service execution is performed by this contract.
