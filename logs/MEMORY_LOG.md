# Memory Log

This log records NEOS runtime memory entries and their links to tasks, events,
states, evidence, audit, incidents, rollback and retention rules.

## Memory entry template

| Field | Value |
|---|---|
| `context_id` | `CTX-NEOS-YYYY-NNN` |
| `timestamp` | ISO 8601 timestamp |
| `memory_category` | `operational_memory`, `task_memory`, `execution_memory`, `decision_memory`, `state_memory`, `evidence_memory`, `incident_memory`, `rollback_memory` or `prohibited_memory` |
| `task_id` | Linked task identifier |
| `event_id` | Linked Event Bus event identifier |
| `state_id` | Linked state identifier |
| `snapshot_id` | Linked snapshot identifier |
| `decision_ref` | Decision log reference |
| `evidence_ref` | Evidence log reference |
| `audit_ref` | Audit trail reference |
| `incident_ref` | Incident log reference |
| `rollback_ref` | Rollback reference |
| `retention_class` | `ephemeral`, `session`, `block`, `phase`, `permanent` or `restricted` |
| `risk_level` | `low`, `medium`, `high` or `critical` |
| `status` | `draft`, `active`, `validated`, `stale`, `deprecated`, `revoked` or `archived` |
| `review_notes` | Human-readable review context |

## Initial Block 6 memory status

| Date | Context ID | Memory Category | Task ID | Event ID | State ID | Snapshot ID | Decision Ref | Evidence Ref | Audit Ref | Incident Ref | Rollback Ref | Retention Class | Risk Level | Status | Review Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-26 | CTX-NEOS-F3-006 | operational_memory | TASK-NEOS-F3-006 | EVT-NEOS-F3-006 | STATE-NEOS-F3-006 | SNAP-NEOS-F3-006 | Decision Log entry for Block 6 | EVD-NEOS-F3-007 | AUD-NEOS-F3-006 | INC-NEOS-F3-006 | Revert Block 6 commit or close PR without merge | block | medium | validated | Block 6 documentary baseline records memory contracts only; no production memory store, business agent, database, secret, permission or dependency change. |
