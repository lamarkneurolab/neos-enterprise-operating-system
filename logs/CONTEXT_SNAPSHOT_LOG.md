# Context Snapshot Log

This log records NEOS execution snapshots used to review context resume and
state recovery decisions.

## Snapshot entry template

| Field | Value |
|---|---|
| `snapshot_id` | `SNAP-NEOS-YYYY-NNN` |
| `execution_id` | Linked execution identifier |
| `task_id` | Linked task identifier |
| `state_id` | Linked state identifier |
| `event_ids` | Linked Event Bus event identifiers |
| `decision_ids` | Linked decision identifiers |
| `evidence_ids` | Linked evidence identifiers |
| `audit_ids` | Linked audit identifiers |
| `incident_ids` | Linked incident identifiers |
| `rollback_ids` | Linked rollback identifiers |
| `created_at` | ISO 8601 timestamp |
| `created_by` | Human or runtime governance actor |
| `reason` | Snapshot reason |
| `resume_allowed` | `true`, `false` or `review_required` |
| `recovery_allowed` | `true`, `false` or `review_required` |
| `risk_level` | `low`, `medium`, `high` or `critical` |
| `validation_status` | `draft`, `valid`, `review_required`, `blocked`, `stale` or `revoked` |

## Initial Block 6 snapshot status

| Date | Snapshot ID | Execution ID | Task ID | State ID | Event IDs | Decision IDs | Evidence IDs | Audit IDs | Incident IDs | Rollback IDs | Created By | Reason | Resume Allowed | Recovery Allowed | Risk Level | Validation Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-26 | SNAP-NEOS-F3-006 | EXEC-NEOS-F3-006 | TASK-NEOS-F3-006 | STATE-NEOS-F3-006 | EVT-NEOS-F3-006 | Decision Log entry for Block 6 | EVD-NEOS-F3-007 | AUD-NEOS-F3-006 | INC-NEOS-F3-006 | Revert Block 6 commit or close PR without merge | Codex / NEOS Runtime Governance | Block 6 context persistence baseline documented. | review_required | review_required | medium | valid |
