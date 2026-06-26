# Audit Closure Record

## Purpose

Define the formal audit record required for documentary closure.

## Minimum structure

- audit_closure_id
- timestamp
- activation_session_id
- monitoring_review_id
- closure_decision_id
- authorized_pr
- authorized_branch
- authorized_head_sha
- base_sha
- closure_scope
- closure_boundary
- evidence_package_reference
- incident_reference
- rollback_reference
- human_approval_reference
- result

## Traceability

The audit closure record must trace authorization, activation, monitoring,
observed events, decisions, evidence, incidents, rollback and closure.

## Prior record integrity

Closure must not modify previous authorization, monitoring, evidence, incident
or audit records. Corrections require new traceable records.

## Closure rule

No closure decision is valid without an audit closure record.
