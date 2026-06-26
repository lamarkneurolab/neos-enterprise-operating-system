# Activation Handoff Rules

## Purpose

Define how a completed activation session may be handed off for future final
review without triggering execution.

## Handoff package

- Activation session record.
- Authorization reference.
- Scope lock.
- Execution window.
- Preconditions verification.
- Pre-activation evidence.
- Pre-activation audit.
- Rollback readiness.
- Monitoring preconditions.
- Go/no-go decision.
- Hold or abort conditions.

## Handoff limits

Handoff does not execute, authorize new scope, extend runtime window, change
permissions, manage secrets, activate integrations, create agents or start
orchestration.

## Invalidation

Any change after handoff to PR, branch, head SHA, commit, scope, action,
runtime window, evidence, audit, rollback readiness or approval requires renewed
review.
