# Dry-Run Pass/Fail Criteria

## Purpose

Define result criteria for dry-run simulation.

## PASS

Dry-run may be marked `PASS` when preflight passes, simulated sequence is
coherent, simulated evidence is sufficient, simulated audit is sufficient,
rollback simulation is ready and no blocking incident remains open.

## FAIL

Dry-run is `FAIL` when the simulated sequence produces an invalid, unsafe,
contradictory or non-compliant outcome.

## BLOCKED

Dry-run is `BLOCKED` when required scope, authorization posture, readiness,
evidence, audit, rollback, incident response or governance/certification input
is missing.

## INCONCLUSIVE

Dry-run is `INCONCLUSIVE` when available simulated evidence is insufficient to
classify the result as pass, fail or blocked.

## Implications

- `PASS` supports review only.
- `FAIL` blocks activation review.
- `BLOCKED` blocks dry-run completion and activation review.
- `INCONCLUSIVE` requires more evidence or review.

## No automatic authorization

No dry-run result authorizes activation automatically.
