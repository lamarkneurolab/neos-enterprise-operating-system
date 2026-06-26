# Context Resume Flow

The Context Resume Flow defines how NEOS may consider resuming execution from
persisted context.

The v0.1.0 resume layer is documentary. It defines verification gates before
resume. It does not resume execution automatically.

## Purpose

Context Resume prevents stale, unauthorized or unaudited memory from
contaminating future execution.

## Minimum resume flow

1. Identify previous execution.
2. Locate the latest valid snapshot.
3. Verify operational state.
4. Verify evidence.
5. Verify audit.
6. Verify open incidents.
7. Confirm memory boundaries.
8. Confirm applicable authorization.
9. Declare context resumable or not resumable.
10. Record the resume decision.

## Resume decision values

| Decision | Meaning |
|---|---|
| `resumable` | Context is valid, current, authorized, evidenced and auditable. |
| `not_resumable` | Context must not be used for resume. |
| `review_required` | Human review is required before resume. |
| `blocked_incident` | An open incident blocks resume. |
| `blocked_evidence` | Required evidence is missing. |
| `blocked_audit` | Required audit linkage is missing. |
| `blocked_authorization` | Applicable authorization is missing or expired. |

## Required checks

| Check | Required evidence |
|---|---|
| Previous execution identified | `execution_id`, `task_id` and state linkage. |
| Snapshot valid | `snapshot_id` with validation status. |
| Operational state valid | State log entry and allowed transition. |
| Evidence complete | Evidence log reference. |
| Audit complete | Audit trail reference. |
| Incidents reviewed | Incident log status. |
| Memory boundaries confirmed | Runtime memory category and prohibited memory review. |
| Authorization applicable | Decision or authorization reference. |

## Critical rule

```text
No execution must resume only because memory exists.
Execution may resume only when memory is valid, traceable, current,
authorized and auditable.
```

## Rules

- Resume must be blocked when critical incidents remain open.
- Resume must be blocked when required evidence or audit linkage is missing.
- Resume must be reviewed when context is high or critical risk.
- Deprecated, revoked or stale context must not be reused without review.
- Resume decisions must be recorded in memory, evidence or audit logs as
  appropriate.

## Non-goals

- No automatic execution resume is introduced.
- No scheduler, worker or external runtime is introduced.
- No production persistence system is introduced.
