# Incident Simulation

## Purpose

Define incident simulation for dry-run orchestration review.

## Simulated incident types

- Missing authorization.
- Missing evidence.
- Missing audit.
- Missing rollback path.
- Preflight failure.
- Invalid simulated state transition.
- External activation attempt.
- Productive orchestration attempt.
- Agent creation attempt.

## Severity

| Severity | Meaning |
|---|---|
| `low` | Documentary inconsistency. |
| `medium` | Missing control that blocks simulation. |
| `high` | Authorization, evidence, audit, rollback or boundary violation. |
| `critical` | Productive activation attempt, prohibited agent creation or severe boundary violation. |

## Escalation

High and critical simulated incidents require human escalation before any
future activation can be considered.

## Response

Incident simulation must record containment, blocker status, rollback
relationship and next action.

## Evidence and registry

Each simulated incident must link simulated evidence, simulated audit and the
simulation result registry.

## Blocking criteria

Open high or critical simulated incidents block activation review.

## Relationship with emergency stop and abort

Incident simulation feeds Block 12 emergency stop and abort conditions. Open or
unresolved incident risk blocks activation authorization.
