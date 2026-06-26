# Execution Snapshot Records

Execution Snapshot Records define the minimum checkpoint used to review,
resume or recover NEOS runtime execution.

The v0.1.0 snapshot layer is documentary. Snapshots preserve references to
runtime facts. They do not execute recovery, resume work automatically or
replace evidence and audit logs.

## Purpose

Execution Snapshots preserve the state of an execution at a reviewable point in
time.

A snapshot must answer:

- What task was active?
- What state was current?
- What events occurred?
- What decisions were active?
- What evidence existed?
- What authorization was active?
- What risks were open?
- What incidents were linked?
- Whether execution was resumable.
- Whether the snapshot was reliable.

## Minimum snapshot record

| Field | Requirement |
|---|---|
| `snapshot_id` | Required unique snapshot identifier. |
| `execution_id` | Linked execution identifier. |
| `task_id` | Linked task identifier. |
| `state_id` | Linked state identifier. |
| `event_ids` | Linked event identifiers. |
| `decision_ids` | Linked decision identifiers. |
| `evidence_ids` | Linked evidence identifiers. |
| `audit_ids` | Linked audit identifiers. |
| `incident_ids` | Linked incident identifiers when applicable. |
| `rollback_ids` | Linked rollback identifiers when applicable. |
| `created_at` | Snapshot timestamp. |
| `created_by` | Human or runtime governance actor creating the snapshot. |
| `reason` | Reason for creating the snapshot. |
| `resume_allowed` | `true`, `false` or `review_required`. |
| `recovery_allowed` | `true`, `false` or `review_required`. |
| `risk_level` | `low`, `medium`, `high` or `critical`. |
| `validation_status` | Current validation status. |

## Validation statuses

| Status | Meaning |
|---|---|
| `draft` | Snapshot captured but not validated. |
| `valid` | Snapshot has required evidence and audit linkage. |
| `review_required` | Snapshot may be useful but needs human review. |
| `blocked` | Snapshot cannot be used because required linkage is missing. |
| `stale` | Snapshot may be outdated. |
| `revoked` | Snapshot must not be used. |

## Rules

- Snapshots must link task, event, state, evidence and audit records.
- Snapshots with open high or critical incidents require review before resume.
- Snapshots lacking evidence must be `blocked` or `review_required`.
- Snapshots contradicted by later decisions must be `stale` or `revoked`.
- A snapshot does not authorize resume by itself.

## Non-goals

- No automated checkpoint engine is introduced.
- No binary snapshot artifact is introduced.
- No database, cache or external storage service is introduced.
