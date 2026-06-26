# Governance Gate Log

This log records governance gate outcomes for NEOS runtime work.

## Governance gate entry template

| Field | Value |
|---|---|
| `gate_log_id` | `GATE-NEOS-YYYY-NNN` |
| `timestamp` | ISO 8601 timestamp |
| `change_type` | Runtime change type under review |
| `risk_level` | `low`, `medium`, `high` or `critical` |
| `required_gate` | Gate applied |
| `evidence_ref` | Evidence log reference |
| `audit_ref` | Audit trail reference |
| `authorization_ref` | Human authorization reference |
| `rollback_ref` | Rollback reference |
| `outcome` | `allowed`, `allowed_with_review`, `blocked` or `rollback_required` |
| `notes` | Human-readable context |

## 2026-06-26 — Fase 3 Block 8

| Date | Gate Log ID | Change Type | Risk Level | Required Gate | Evidence Ref | Audit Ref | Authorization Ref | Rollback Ref | Outcome | Notes |
|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-26 | GATE-NEOS-F3-009 | Runtime certification and governance documentation | medium | Certification Gates, Governance Gate Matrix, Pre-merge Governance Review, Runtime Compliance Checklist, Readiness Certifications, Evidence and Audit Sufficiency, Human Authorization, Critical Decision, Release Candidate Review | EVD-NEOS-F3-009 | AUD-NEOS-F3-008 | Tiziano authorization to initiate Block 8; merge authorization not granted | Revert Block 8 commit or close PR without merge | allowed_with_review | Documentation can be proposed in PR; merge remains blocked until explicit Tiziano authorization for the specific PR. |
