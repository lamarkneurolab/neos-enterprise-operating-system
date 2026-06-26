# Governance Gate Validation

## Purpose

Validate that Block 8 governance gates correctly block or allow runtime work.

## Scope

Governance Gate Matrix, Pre-merge Governance Review, Human Authorization Gates,
Critical Decision Gates, blocking governance conditions and PR-specific
authorization.

## Related runtime components

Governance Gate Matrix, Pre-merge Governance Review, Human Authorization Gates,
Critical Decision Gates, Governance Gate Log and Decision Log.

## Validation model

| Scenario | Expected validation |
|---|---|
| Matrix lookup | Change type maps to required gates and logs. |
| Pre-merge review | Required review checks pass before merge consideration. |
| Human authorization | Required human authorization is exact and current. |
| Critical decision | Critical decisions are logged and audited. |
| Blocking condition | Missing evidence/audit/rollback/authorization blocks closure. |
| PR-specific authorization | Prior PR authorization is not reused. |

## Required evidence

Governance gate log entry, decision reference and validation result.

## Required audit trail

Audit is required for governance decisions affecting closure, merge, rollback,
critical decisions or release readiness.

## Pass criteria

Governance matrix is applied, required gates are identified and authorization
requirements are respected.

## Fail criteria

Change bypasses matrix, omits critical decision, reuses prior authorization or
lacks required evidence/audit.

## Blocking conditions

Any missing required governance element blocks merge and release readiness.

## Rollback considerations

Revert governance change, restore prior gate language or close PR without
merge.

## Human authorization requirements when applicable

Required for every merge, critical decision, critical rollback, dependency,
permission, secret, destructive or external action.

## Related certification/governance gates

Human Authorization Requirement, Critical Decision Escalation, Evidence
Sufficiency, Audit Sufficiency and Release Candidate Readiness.

## Minimum checklist

- [ ] Change type classified.
- [ ] Matrix row identified.
- [ ] Required gates listed.
- [ ] Evidence linked.
- [ ] Audit linked when required.
- [ ] Human authorization checked.
