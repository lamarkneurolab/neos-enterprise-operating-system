# Incident Log

This log records NEOS runtime incidents, blocked conditions, degraded
conditions and manual intervention requirements.

## Incident entry template

| Field | Value |
|---|---|
| `incident_id` | `INC-NEOS-YYYY-NNN` |
| `timestamp` | ISO 8601 timestamp |
| `severity` | `info`, `warning`, `error` or `critical` |
| `affected_component` | Runtime component affected |
| `task_id` | Linked task identifier |
| `event_id` | Linked Event Bus event identifier |
| `description` | Human-readable incident summary |
| `detected_by` | Human, runtime component or review process |
| `risk_level` | `low`, `medium`, `high` or `critical` |
| `containment_action` | Immediate containment or stop condition |
| `rollback_required` | `true`, `false` or `not_required` |
| `rollback_ref` | Rollback reference |
| `evidence_ref` | Evidence log reference |
| `audit_ref` | Audit trail reference |
| `status` | `open`, `triaged`, `contained`, `resolved`, `rollback_required` or `closed` |

## Initial Block 5 status

| Date | Incident ID | Severity | Affected Component | Task ID | Event ID | Description | Detected By | Risk Level | Containment Action | Rollback Required | Rollback Ref | Evidence Ref | Audit Ref | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-25 | INC-NEOS-F3-000 | info | runtime-observability-audit-trail | TASK-NEOS-F3-005 | EVT-NEOS-F3-005 | Block 5 incident log initialized; no runtime incident recorded during documentation baseline. | Codex / NEOS Runtime Governance | low | not_required | not_required | not_required | EVD-NEOS-F3-006 | AUD-NEOS-F3-005 | closed |

## Initial Block 6 status

| Date | Incident ID | Severity | Affected Component | Task ID | Event ID | Description | Detected By | Risk Level | Containment Action | Rollback Required | Rollback Ref | Evidence Ref | Audit Ref | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-26 | INC-NEOS-F3-006 | info | runtime-memory-context-persistence | TASK-NEOS-F3-006 | EVT-NEOS-F3-006 | Block 6 memory and context snapshot logs initialized; no runtime incident recorded during documentation baseline. | Codex / NEOS Runtime Governance | low | not_required | not_required | not_required | EVD-NEOS-F3-007 | AUD-NEOS-F3-006 | closed |

## Initial Block 7 status

| Date | Incident ID | Severity | Affected Component | Task ID | Event ID | Description | Detected By | Risk Level | Containment Action | Rollback Required | Rollback Ref | Evidence Ref | Audit Ref | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-26 | INC-NEOS-F3-007 | info | runtime-sdk-integration-contracts | TASK-NEOS-F3-007 | EVT-NEOS-F3-007 | Block 7 SDK and integration contract logs initialized; no runtime incident recorded during documentation baseline. `runtime/authorization.md` was not present, so Block 7 links to existing authorization documentation instead. | Codex / NEOS Runtime Governance | low | not_required | not_required | not_required | EVD-NEOS-F3-008 | AUD-NEOS-F3-007 | closed |

## Initial Block 8 status

| Date | Incident ID | Severity | Affected Component | Task ID | Event ID | Description | Detected By | Risk Level | Containment Action | Rollback Required | Rollback Ref | Evidence Ref | Audit Ref | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-26 | INC-NEOS-F3-008 | info | runtime-certification-governance-gates | TASK-NEOS-F3-008 | EVT-NEOS-F3-008 | Block 8 certification, governance and release candidate logs initialized; no runtime incident recorded during documentation baseline. Merge remains blocked until explicit Tiziano authorization for the specific PR. | Codex / NEOS Runtime Governance | low | not_required | not_required | not_required | EVD-NEOS-F3-009 | AUD-NEOS-F3-008 | closed |

## Initial Block 9 status

| Date | Incident ID | Severity | Affected Component | Task ID | Event ID | Description | Detected By | Risk Level | Containment Action | Rollback Required | Rollback Ref | Evidence Ref | Audit Ref | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-26 | INC-NEOS-F3-009 | info | runtime-testing-validation-harness | TASK-NEOS-F3-009 | EVT-NEOS-F3-009 | Block 9 testing, validation, evidence, audit, regression and release readiness validation logs initialized; no runtime incident recorded during documentation baseline. Merge remains blocked until explicit Tiziano authorization for the specific PR. | Codex / NEOS Runtime Governance | low | not_required | not_required | not_required | EVD-NEOS-F3-010 | AUD-NEOS-F3-009 | closed |
