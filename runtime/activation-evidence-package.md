# Activation Evidence Package

## Purpose

Define the minimum evidence package for activation requests.

## Minimum package

- Activation request.
- Dry-run simulation result.
- Simulation evidence.
- Simulation audit.
- Rollback plan.
- Incident plan.
- Risk acceptance record.
- Human approval decision.
- Scope definition.
- Abort conditions.

## Relationship with Block 11 logs

The package must link:

- `logs/DRY_RUN_SIMULATION_LOG.md`
- `logs/SIMULATION_RESULT_REGISTRY_LOG.md`
- `logs/PREFLIGHT_CHECK_LOG.md`
- `logs/SIMULATED_ROLLBACK_LOG.md`
- `logs/INCIDENT_SIMULATION_LOG.md`

## Relationship with core logs

The package must link `logs/AUDIT_TRAIL.md`, `logs/EVIDENCE_LOG.md` and
`logs/DECISION_LOG.md`.

## Sufficiency criteria

Evidence is sufficient when it is specific, current, traceable, scoped to the
request and linked to audit and decision records.
