# Unresolved Risk Register

## Purpose

Define the register for unresolved risks after monitoring.

## Minimum fields

- risk_id
- severity
- owner
- impact
- affected_scope
- evidence_reference
- audit_reference
- incident_reference
- rollback_reference
- residual_risk_decision
- human_approval_reference

## Severity

- low
- medium
- high
- critical

## Human acceptance

Residual risk may be accepted only through explicit human approval that names
the PR, branch, head SHA, closure scope and closure boundary.

## Blocking rule

Critical unresolved risk blocks closure unless explicitly escalated and accepted
under the approved governance process.
