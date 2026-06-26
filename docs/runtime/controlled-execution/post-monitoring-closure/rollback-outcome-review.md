# Rollback Outcome Review

## Purpose

Define how rollback outcome is reviewed before closure.

## Rollback states

- not_required
- required_but_not_executed
- executed_documentarily
- failed
- pending_authorization

## Blocking criteria

Closure is blocked when critical rollback is required but pending, failed,
unauthorized, unaudited or unsupported by evidence.

## Evidence required

- rollback_reference
- rollback_trigger
- rollback_decision
- rollback_evidence
- rollback_audit
- rollback_result
- human_authorization_when_required

## Relationship with closure

Rollback outcome must be resolved, accepted or escalated before closure can be
approved.
