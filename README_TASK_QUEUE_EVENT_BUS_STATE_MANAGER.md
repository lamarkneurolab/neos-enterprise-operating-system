# NEOS Task Queue, Event Bus & State Manager v0.1.0

This document is the operational entry point for NEOS Block 4: Task Queue,
Event Bus & State Manager.

Block 4 organizes, traces and governs runtime execution. It does not execute
business agents, implement production workers or introduce real external
services such as Kafka, Redis, RabbitMQ or a database.

## Objective

Create the minimum runtime coordination layer for NEOS Enterprise AI Platform:

- Register tasks in a Task Queue contract.
- Emit internal runtime events through an Event Bus contract.
- Govern execution states through a State Manager contract.
- Record execution state changes in an Execution State Log.
- Link tasks, events, state records, evidence, audit and rollback.

## Components included

| Component | Purpose |
|---|---|
| Task Queue | Records task metadata and execution status. |
| Event Bus | Defines internal event records for runtime traceability. |
| State Manager | Defines valid and blocked task state transitions. |
| Execution State Log | Records lifecycle state changes for review. |
| Rollback Hooks | Declares rollback evaluation and closure requirements. |
| Audit Linkage | Connects runtime records to decisions and evidence. |

## Operational flow

```text
Authorization Flow
  -> Task Queue
  -> Event Bus
  -> State Manager
  -> Execution State Log
  -> Evidence / Audit / Rollback
```

Authorized work enters the Runtime Coordination Layer as a task record. The
task emits events, transitions through the State Manager, records each state
change and preserves evidence, audit and rollback references.

Blocked or rejected work must not enter `in_progress`.

## Files created

| File | Purpose |
|---|---|
| `README_TASK_QUEUE_EVENT_BUS_STATE_MANAGER.md` | Block 4 entry point. |
| `docs/execution-layer/task-queue-event-bus-state-manager-v0.1.0.md` | Canonical Block 4 specification. |
| `runtime/task-queue.md` | Task Queue contract. |
| `runtime/event-bus.md` | Event Bus contract. |
| `runtime/state-manager.md` | State Manager contract. |
| `logs/EXECUTION_STATE_LOG.md` | Execution state transition log. |

## Files modified

| File | Change |
|---|---|
| `docs/execution-layer/execution-engine.md` | Adds Runtime Coordination Layer rules. |
| `docs/execution-layer/authorization-flow.md` | Adds handoff rules after authorization. |
| `logs/DECISION_LOG.md` | Records the Block 4 governance decision. |
| `logs/EVIDENCE_LOG.md` | Records the Block 4 evidence entry. |

## Acceptance criteria

Block 4 v0.1.0 is accepted when:

1. The required Block 4 files exist.
2. Task Queue, Event Bus and State Manager contracts are documented.
3. Valid and blocked transitions are documented.
4. Rollback hooks and audit linkage are documented.
5. Decision and evidence logs are updated.
6. No business agents are created.
7. No production workers are introduced.
8. No external service implementation is introduced.
9. Markdown and Git diff validation pass.
10. A Draft PR is opened for human review.
11. No automatic merge is performed.

## Initial status v0.1.0

Block 4 v0.1.0 is a documentation and traceability baseline. It establishes
runtime coordination contracts only. It is not an autonomous execution engine
and does not provide queue storage, event transport, worker execution or
database persistence.

## Restrictions

- GitHub is the canonical source.
- Markdown `.md` is the official source format.
- Google Drive may only mirror visual or documentary material.
- No business agents are created.
- No production workers are implemented.
- No Kafka, Redis, RabbitMQ, database or external service is introduced.
- No automatic merge is performed.
- Every execution must preserve evidence, audit and rollback traceability.
