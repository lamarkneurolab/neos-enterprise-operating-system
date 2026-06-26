# Controlled Activation Preconditions

## Purpose

Define documentary preconditions required before any future controlled
activation can be considered.

## Separation rule

Simulation approved is not activation approved.

Dry-run passed is not activation approved.

Activation requires a separate authorization and review for the exact scope.

## Minimum evidence

- Release readiness reference.
- Orchestration readiness reference.
- Dry-run simulation result.
- Simulated evidence and audit review.
- Rollback simulation review.
- Incident simulation review.
- Human authorization record.

## Human validation

Human validation must confirm scope, risk, branch, PR, head SHA, commit,
allowed action and expiration/scope limit.

## Residual risks

Residual risks must identify any unresolved blocker, unknown external effect,
rollback uncertainty, audit gap, evidence gap or incident escalation.

## Requirements before future Block 12

Before any future activation-focused block, NEOS must have completed dry-run
simulation review, documented residual risks and recorded explicit human
authorization requirements.

## Relationship with Block 12

Block 12 formalizes these preconditions into controlled activation gate,
activation request, risk acceptance, evidence package, audit requirements and
execution authorization records.
