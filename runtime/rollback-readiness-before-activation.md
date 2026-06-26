# Rollback Readiness Before Activation

## Purpose

Define rollback readiness as a required precondition before future controlled
activation.

## Minimum rollback readiness

- rollback_reference
- rollback_owner_or_reviewer
- rollback_trigger
- rollback_action
- rollback_evidence_required
- rollback_audit_required
- non_rollbackable_constraints
- completion_criteria

## Readiness rule

Rollback readiness must be documented before activation is considered. It is not
a late reaction after execution begins.

## Blocking conditions

Missing rollback plan, missing evidence, unclear trigger, unresolved high risk
or non-rollbackable action without explicit risk acceptance blocks go/no-go.
