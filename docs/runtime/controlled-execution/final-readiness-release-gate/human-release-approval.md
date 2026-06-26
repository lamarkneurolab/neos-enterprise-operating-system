# Human Release Approval

## Purpose

Define the explicit human approval required before any future release gate go
decision.

## Scope

Human release approval applies only to the exact release gate request under
review.

## Required inputs

- PR.
- Branch.
- Head SHA.
- Commit.
- Scope.
- Action.
- Runtime window.
- Monitoring boundary.
- Closure boundary.
- Release boundary.
- Final readiness certification.
- Evidence package.
- Audit integrity certification.
- Risk, rollback and incident certifications.

## Expected outputs

- human_release_decision
- authorizer
- approval_scope
- expiration_or_limit
- evidence_reference
- audit_reference

## Control rules

Approval must be explicit, scoped and non-reusable.

## Evidence minimum

Approval evidence must name authorizer, PR, branch, head SHA, commit, scope,
action, runtime window, monitoring boundary, closure boundary and release
boundary.

## Acceptance criteria

Approval is valid only when it matches the exact release gate request.

## Invalidity conditions

Approval is invalid when any named field changes or evidence is incomplete.

## Governance relationship

Human release approval is required for release gate go decisions.

## Non-production rule

Human approval is required, but approval still does not execute runtime unless a
future separately authorized action exists.
