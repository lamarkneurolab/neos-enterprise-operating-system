# Release-to-Orchestration Criteria

## Purpose

Define criteria for considering whether a future capability can move from
release readiness to orchestration readiness review.

## Minimum requirements

- Validation completed.
- Evidence sufficient.
- Audit sufficient.
- Rollback documented.
- Incident response mapped.
- Human authorization status resolved.
- No unresolved governance blockers.
- No unresolved certification blockers.
- No productive orchestration activated in documentary review.
- No prohibited agent, external integration, dependency, permission change,
  secret management, runner, service, queue or database introduced.

## Output states

| State | Meaning |
|---|---|
| `blocked` | Required validation, evidence, audit, rollback, authorization or gate outcome is missing or failed. |
| `needs_review` | Inputs exist but require review before eligibility. |
| `eligible_for_orchestration_review` | Documentary requirements are sufficient for orchestration review. |
| `authorization_required` | Human authorization is required before approval. |
| `approved_for_controlled_orchestration` | Specific controlled orchestration is approved for the documented scope. |

## Transition rule

Release readiness may feed orchestration readiness review, but it does not
approve orchestration. Approval requires the specific authorization and control
records required by the future scope.

## Relationship with release-to-activation

Release-to-orchestration may feed dry-run simulation, but it does not approve
activation. Future activation must satisfy controlled activation
preconditions, including dry-run simulation result review and explicit human
authorization for the exact scope.
