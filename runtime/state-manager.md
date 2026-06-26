# State Manager Contract

The State Manager contract defines the minimum state governance model used by
the NEOS Runtime Coordination Layer.

The v0.1.0 State Manager validates transitions as a documented contract. It is
not a production state machine service or database.

## Purpose

The State Manager prevents runtime execution from skipping authorization,
evidence, audit or rollback requirements.

## Minimum state record

| Field | Requirement |
|---|---|
| `state_id` | Required unique state record identifier. |
| `task_id` | Linked task identifier. |
| `current_state` | Current task state. |
| `allowed_next_states` | Permitted next states. |
| `blocked_transitions` | Prohibited transitions. |
| `required_authorization` | Authorization required for transition. |
| `required_evidence` | Evidence required for transition or closure. |
| `rollback_condition` | Condition that triggers rollback. |
| `failure_condition` | Condition that marks failure. |

## Valid transitions

| Previous state | Next state |
|---|---|
| `queued` | `authorized` |
| `queued` | `blocked` |
| `authorized` | `in_progress` |
| `authorized` | `cancelled` |
| `blocked` | `cancelled` |
| `in_progress` | `completed` |
| `in_progress` | `failed` |
| `failed` | `rollback_requested` |
| `rollback_requested` | `rolled_back` |
| `rollback_requested` | `failed` |

## Blocked transitions

| Previous state | Blocked next state | Reason |
|---|---|---|
| `queued` | `in_progress` | Authorization must be recorded first. |
| `queued` | `completed` | Execution states must not be skipped. |
| `blocked` | `in_progress` | Blocked tasks cannot execute. |
| `failed` | `completed` | Failed tasks require remediation. |
| `completed` | `in_progress` | Completed tasks are closed. |
| `cancelled` | `in_progress` | Cancelled tasks require a new task. |
| `rolled_back` | `completed` | Rolled back tasks close as rollback records. |

## Rules

- Runtime must not skip states.
- Every state transition must be logged.
- Invalid transitions must be blocked.
- Invalid transitions must be inspectable through Runtime Observability.
- Invalid transitions must link an incident record when closure is blocked.
- Rollback states require evidence before closure.
- Resume and recovery decisions require valid memory and snapshot review before
  state is treated as current.
- `queued` tasks cannot enter `in_progress` directly.
- `blocked` or rejected tasks cannot enter `in_progress`.
- `completed`, `cancelled` and `rolled_back` are terminal for the original
  task record.

## Required authorization

The transition from `authorized` to `in_progress` requires:

- Authorization outcome set to `Authorized`.
- Required permission references.
- Required capability references.
- Evidence requirement identified for medium, high and critical work.

## Required evidence

Evidence is required before closing:

- Medium risk tasks.
- High risk tasks.
- Critical risk tasks.
- Failed tasks.
- Rollback requested tasks.
- Rollback completed tasks.

## Rollback condition

Rollback must be evaluated when:

- Repository content changes.
- External systems are modified.
- Verification fails after partial execution.
- The task fails after side effects were produced.
- Human review requests rollback.

## Failure condition

A task enters `failed` when:

- Execution cannot complete.
- Verification fails.
- Required evidence cannot be produced.
- Required audit linkage cannot be produced.
- Rollback cannot complete from `rollback_requested`.

## Observability and incident linkage

State transitions should preserve Block 5 links when applicable:

| State condition | Required Block 5 link |
|---|---|
| Valid transition | Observability event and Event Bus event. |
| Invalid transition | `invalid_state_transition` incident. |
| Missing evidence | `missing_evidence` incident. |
| Missing audit | `missing_audit_entry` incident. |
| Rollback failure | `rollback_failure` incident. |
| Manual remediation | `manual_intervention_required` incident. |
| Context resume | Memory record, snapshot record, evidence and audit link. |
| State recovery | Snapshot record, evidence, audit and incident review. |

Observability and incident records do not change state by themselves. They
preserve the review trail for state decisions already governed by this contract.

## Memory and recovery linkage

State recovery must not bypass State Manager rules. A prior state may be used
only when linked memory and snapshots are valid, evidenced, audited and not
blocked by open high or critical incidents.

State records that are stale, deprecated, revoked or missing evidence must not
be recovered as current operational truth.

## SDK and integration linkage

SDK invocations and integration entry points must follow the same state rules
as other runtime work.

| Condition | State rule |
|---|---|
| SDK invocation requested | Task must already be `authorized`. |
| Integration entry requested | Registry, authorization and boundary checks must be complete. |
| External execution blocked | Move to `blocked` or `failed` with evidence. |
| Contract validation failed | Move to `failed` and link incident when closure is affected. |
| Rollback required | Move through `rollback_requested` before `rolled_back`. |

No SDK or integration contract may move a task directly from `queued` to
`in_progress` or from `failed` to `completed`.

## Non-goals

- No production state machine service is implemented.
- No database persistence is introduced.
- No worker execution is introduced.
- No automatic memory-based recovery is introduced.
