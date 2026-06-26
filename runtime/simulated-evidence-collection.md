# Simulated Evidence Collection

## Purpose

Define simulated evidence for dry-run and no-op review.

## Simulated evidence

Simulated evidence documents what would be observed during future execution.
It is not proof that real execution happened.

## Minimum fields

| Field | Requirement |
|---|---|
| `simulated_evidence_id` | Stable simulated evidence identifier. |
| `dry_run_id` | Linked dry-run identifier. |
| `scope` | Simulated scope. |
| `input_reference` | Readiness, playbook or preflight input. |
| `simulated_step` | Step under review. |
| `expected_observation` | Expected simulated observation. |
| `result` | Simulated result. |
| `reviewer` | Reviewer. |
| `notes` | Notes and limitations. |

## Difference from real evidence

Simulated evidence supports review only. Real activation would require real
execution evidence created during the authorized activation scope.

## Log relationship

Simulated evidence is referenced from `logs/DRY_RUN_SIMULATION_LOG.md` and
`logs/SIMULATION_RESULT_REGISTRY_LOG.md`.

## Sufficiency criteria

Simulated evidence is sufficient when it is specific, current, traceable,
clearly labeled as simulated and linked to simulated audit.
