# Authorization Flow Validation

## Purpose

Validate that authorization gates correctly allow, deny or block runtime work.

## Scope

Human authorization required, authorization denied, authorization missing,
authorization expired, unauthorized execution blocked, critical decision gate
required and merge authorization required.

## Related runtime components

Authorization Flow, Human Authorization Gates, Critical Decision Gates,
Pre-merge Governance Review and Decision Log.

## Validation model

| Scenario | Expected validation |
|---|---|
| Human authorization required | Action blocks until explicit authorization exists. |
| Authorization denied | Action remains blocked and does not proceed. |
| Authorization missing | Action reports blocked authorization. |
| Authorization expired | Action requires renewed authorization. |
| Unauthorized execution | Execution, merge or external action is blocked. |
| Critical decision required | Decision is logged before closure or merge. |
| Merge authorization | Merge requires PR-specific Tiziano authorization. |

## Required evidence

Authorization reference, decision reference, PR reference or blocked condition
evidence.

## Required audit trail

Audit is required for merge authorization, critical decision, denied
authorization and blocked high/critical actions.

## Pass criteria

Required authorization is specific, current, linked and sufficient for the exact
action.

## Fail criteria

Authorization is missing, stale, broad, inherited from a prior PR or not tied to
the exact action.

## Blocking conditions

Missing PR-specific merge authorization, unauthorized external action,
permission change, secret handling, destructive action or dependency install
blocks execution and merge.

## Rollback considerations

Stop the action, close the PR without merge, revert unauthorized documentation
change or record incident when needed.

## Human authorization requirements when applicable

Tiziano authorization is mandatory for merge, dependencies, permissions,
secrets, deletion, destructive action, external activation, critical rollback
and release approval.

## Related certification/governance gates

Human Authorization Requirement, Critical Decision Escalation, Pre-merge
Governance Review and Release Candidate Readiness.

## Minimum checklist

- [ ] Authorization status identified.
- [ ] Exact action named.
- [ ] PR-specific merge authorization checked.
- [ ] Critical decision checked.
- [ ] Evidence linked.
- [ ] Audit linked when required.
