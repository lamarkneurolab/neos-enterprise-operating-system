# Simulation Layer

## Purpose

Define the NEOS runtime simulation layer for documentary dry-run review.

## Layer definition

The simulation layer records simulated orchestration intent, simulated state,
simulated results, simulated evidence, simulated audit, simulated rollback and
simulated incidents.

## Separation from real runtime

The simulation layer must not mutate real runtime state, call real
integrations, change permissions, manage secrets, create services or activate
productive orchestration.

## Limits

- Documentary only.
- No external side effects.
- No production state mutation.
- No dependency installation.
- No runner or CI creation.
- No business agent creation.

## Simulated states

| State | Meaning |
|---|---|
| `simulation_not_started` | Required preflight inputs are not complete. |
| `preflight_ready` | Preflight inputs are available for review. |
| `simulation_running` | Documentary simulation is being reviewed. |
| `simulation_passed` | Simulated criteria passed. |
| `simulation_failed` | Simulated criteria failed. |
| `simulation_blocked` | Required control is missing or prohibited action detected. |
| `simulation_inconclusive` | Result cannot be interpreted. |

## Traceability

Every simulation must link inputs, preflight result, simulated evidence,
simulated audit, rollback simulation, incident simulation and final result.

## Conditions of invalidity

A simulation is invalid when it uses stale inputs, lacks traceability, relies
on real side effects, omits required evidence or implies activation approval.
