# Certification Log

This log records NEOS certification gate evaluations.

## Certification entry template

| Field | Value |
|---|---|
| `certification_id` | `CERT-NEOS-YYYY-NNN` |
| `timestamp` | ISO 8601 timestamp |
| `gate` | Certification gate name |
| `task_id` | Linked task identifier |
| `event_id` | Linked Event Bus event identifier |
| `scope` | Files, contracts or runtime component reviewed |
| `evidence_ref` | Evidence log reference |
| `audit_ref` | Audit trail reference |
| `decision_ref` | Decision log reference |
| `rollback_ref` | Rollback reference |
| `result` | `certified`, `certified_with_review`, `blocked` or `rollback_required` |
| `notes` | Human-readable context |

## 2026-06-26 — Fase 3 Block 8

| Date | Certification ID | Gate | Task ID | Event ID | Scope | Evidence Ref | Audit Ref | Decision Ref | Rollback Ref | Result | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-26 | CERT-NEOS-F3-009 | Runtime Certification & Governance Gates v0.1.0 | TASK-NEOS-F3-008 | EVT-NEOS-F3-008 | Block 8 certification gates, governance matrix, readiness certifications, sufficiency rules, human authorization gates, critical decision gates and release candidate review | EVD-NEOS-F3-009 | AUD-NEOS-F3-008 | Decision Log entry for Block 8 | Revert Block 8 commit or close PR without merge | certified_with_review | Certification is documentary and remains subject to PR review and explicit Tiziano merge authorization for the specific PR. |
