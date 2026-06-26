# Evidence Collection Playbooks

## Purpose

Define minimum evidence collection requirements for future controlled
orchestration.

## Evidence by action type

| Action type | Minimum evidence |
|---|---|
| Documentation change | Changed file list, diff check result and reviewer notes. |
| Validation review | Scenario, result, evidence reference and audit reference. |
| Readiness review | Scope, readiness status, validation, evidence, audit and rollback references. |
| Authorization decision | Authorizer, scope, branch, PR, head SHA when applicable, allowed action and expiration/scope limit. |
| Rollback | Trigger, rollback steps, result, evidence and audit references. |
| Incident response | Incident ID, severity, trigger, containment, rollback link, audit link and evidence link. |

## Evidence timing

| Timing | Required evidence |
|---|---|
| Before execution | Scope, validation mapping, authorization status, rollback plan and evidence plan. |
| During execution | Step outputs, state changes, audit events, incidents and deviations. |
| After execution | Verification result, final state, evidence sufficiency, audit sufficiency and completion review. |

## Log relationships

Evidence collection must reference:

- `logs/TEST_EVIDENCE_LOG.md` for validation evidence.
- `logs/EVIDENCE_LOG.md` for broader execution evidence.
- `logs/ORCHESTRATION_READINESS_LOG.md` for readiness review evidence.

## Evidence sufficiency for readiness

Evidence is sufficient only when it is specific, current, reviewable,
traceable to scope and linked to audit when governance-relevant.

## Blocking conditions

Missing, stale, ambiguous, fabricated or scope-mismatched evidence blocks
readiness, approval and closure.

## Relationship with simulated evidence

Block 11 simulated evidence supports dry-run review only. Simulated evidence
must be labeled as simulated and must not be treated as proof of real
execution.
