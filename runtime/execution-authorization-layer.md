# Execution Authorization Layer

## Purpose

Define the authorization model required before any future execution.

## Model

Execution authorization is a scoped human decision that may permit a future
execution request to proceed. It does not execute by itself.

## Limits

- Authorization applies only to the documented scope.
- Authorization applies only to the specific PR, branch, head SHA, commit and
  action.
- Authorization cannot be reused.
- Authorization does not override evidence, audit, rollback or incident
  requirements.

## Human authority

Explicit human approval is required when future execution, merge, activation,
risk acceptance, exception or critical action is requested.

## Invalidation conditions

Authorization is invalid when any of these changes:

- PR.
- Branch.
- Head SHA.
- Commit.
- Scope.
- Requested action.
- Risk level.
- Evidence package.
- Audit package.

## Required record

Every authorization, denial, deferral, block or abort decision must be recorded
in `logs/EXECUTION_AUTHORIZATION_LOG.md` and linked to audit and decision logs.

## Block 13 transition

Execution authorization is followed by the Block 13 controlled execution
activation protocol. Authorization does not execute by itself and remains
insufficient without activation session, scope lock, execution window,
pre-activation evidence, audit record, rollback readiness and explicit human
go/no-go.
