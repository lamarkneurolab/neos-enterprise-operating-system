# Audit Record Before Activation

## Purpose

Define the audit record required before a future controlled activation can be
considered.

## Minimum audit fields

- audit_id
- timestamp
- activation_session_id
- authorization_reference
- decision_reference
- PR
- branch
- head SHA
- commit
- scope
- action
- runtime window
- evidence_reference
- rollback_reference
- risk_level
- result
- notes

## Audit rule

No activation session can proceed to go/no-go review without a pre-activation
audit record.

## Relationship to audit trail

Governance-relevant activation audit belongs in `logs/AUDIT_TRAIL.md` and must
link to the activation session and pre-activation evidence records.
