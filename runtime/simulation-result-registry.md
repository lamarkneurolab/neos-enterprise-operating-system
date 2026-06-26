# Simulation Result Registry

## Purpose

Define registry rules for dry-run and simulation results.

## Minimum fields

| Field | Requirement |
|---|---|
| `simulation_id` | Stable simulation identifier. |
| `date` | ISO 8601 date. |
| `scope` | Simulated scope. |
| `dry_run_reference` | Dry-run record reference. |
| `preflight_reference` | Preflight result reference. |
| `simulated_evidence_reference` | Simulated evidence reference. |
| `simulated_audit_reference` | Simulated audit reference. |
| `rollback_reference` | Simulated rollback reference. |
| `incident_reference` | Incident simulation reference. |
| `status` | `PASS`, `FAIL`, `BLOCKED` or `INCONCLUSIVE`. |
| `risk` | Risk level. |
| `decision` | Review decision. |
| `next_action` | Required follow-up. |

## Log relationship

Registry entries are recorded in
`logs/SIMULATION_RESULT_REGISTRY_LOG.md`.

## Rule

Simulation result registry status does not authorize activation. Activation
requires separate human authorization for the exact future scope.

## Relationship with activation requests

Simulation registry entries may be linked from activation requests. A changed
simulation result requires activation request review and may require a new
simulation.
