# Emergency Stop / Abort Log

This log records NEOS emergency stop and abort reviews.

## Purpose

Track abort conditions, emergency stop conditions, invalidated authorization
and human escalation.

## Scope

Abort and emergency stop review for controlled activation and future execution.

## Entry template

| Date | Abort ID | Request ID | Scope | Trigger | Status | Evidence | Audit | Escalation | Notes |
|---|---|---|---|---|---|---|---|---|---|
| ISO 8601 date | Abort identifier | Request ID | Scope | Trigger | `not_required`, `aborted`, `blocked` or `escalated` | Evidence reference | Audit reference | Escalation | Notes |

## 2026-06-26 - Fase 3 Block 12

| Date | Abort ID | Request ID | Scope | Trigger | Status | Evidence | Audit | Escalation | Notes |
|---|---|---|---|---|---|---|---|---|---|
| 2026-06-26 | ABORT-NEOS-F3-012 | ACT-REQ-NEOS-F3-012 | Runtime Controlled Activation Gate & Execution Authorization Layer v0.1.0 | Activation or merge attempted without explicit authorization | blocked | TEST-EVD-NEOS-F3-012 | AUD-NEOS-F3-012 | Tiziano authorization required | Documentary baseline only; no emergency stop executed. |
| 2026-06-26 | ABORT-NEOS-F3-013 | ACT-REQ-NEOS-F3-013 | Runtime Controlled Execution Activation Protocol v0.1.0 | Runtime activation, go decision or merge attempted without explicit authorization | blocked | PRE-ACT-EVD-NEOS-F3-013 | AUD-NEOS-F3-013 | Tiziano authorization required | Documentary baseline only; no emergency stop executed. |

## v0.1.0 status

Future entries must be traceable and auditable.
