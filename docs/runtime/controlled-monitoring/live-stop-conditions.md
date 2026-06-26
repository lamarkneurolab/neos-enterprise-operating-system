# Live Stop Conditions

## Purpose

Define conditions that must stop future controlled execution.

## Stop conditions

- Scope drift.
- Unauthorized action.
- Runtime window breach.
- Monitoring boundary breach.
- Missing evidence.
- Missing audit.
- Critical health degradation.
- Critical safety signal breach.
- Rollback readiness failure.
- Human go/no-go mismatch.
- Secret, permission, dependency, service, runner, CI, database or integration
  change outside authorization.

## Stop outcome

Stop halts continuation and requires evidence, audit, human review and rollback
assessment.

## Non-execution rule

This document defines stop conditions only. It does not implement automated
stopping or execute runtime controls.
