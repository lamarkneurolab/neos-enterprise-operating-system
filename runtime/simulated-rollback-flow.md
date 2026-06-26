# Simulated Rollback Flow

## Purpose

Define rollback simulation for dry-run orchestration review.

## Definition

Simulated rollback rehearses rollback triggers and expected rollback outcomes
without changing real state.

## States

| State | Meaning |
|---|---|
| `rollback-ready` | Rollback path is documented and simulated evidence is sufficient. |
| `rollback-blocked` | Rollback path is missing, unsafe or lacks authorization posture. |
| `rollback-incomplete` | Rollback simulation lacks evidence, audit or completion criteria. |

## Evidence required

- Rollback trigger.
- Affected simulated scope.
- Expected prior state.
- Simulated rollback steps.
- Simulated result.
- Simulated audit reference.

## Failure conditions

Rollback simulation fails when trigger, scope, prior state, evidence, audit,
completion criteria or human escalation condition is missing.

## Log relationship

Simulated rollback reviews are recorded in `logs/SIMULATED_ROLLBACK_LOG.md`.

## Relationship with activation rollback controls

Simulated rollback may support an activation request only when rollback scope,
evidence and audit are linked to the activation evidence package.
