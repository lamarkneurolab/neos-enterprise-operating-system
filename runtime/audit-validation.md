# Audit Validation

## Purpose

Validate audit sufficiency for runtime testing, governance and release
readiness.

## Scope

Audit required, sufficient, missing, invalid, stale, linked to evidence, linked
to authorization and linked to rollback.

## Related runtime components

Audit Trail, Decision Log, Evidence Log, Test Evidence Log, Governance Gate Log,
Certification Log and Release Readiness Validation.

## Validation model

| Scenario | Expected validation |
|---|---|
| Audit required | Required audit condition is named. |
| Audit sufficient | Audit links action, actor, evidence and decision. |
| Audit missing | Closure and readiness block. |
| Audit invalid | Audit is rejected. |
| Audit stale | Audit requires refresh. |
| Evidence linkage | Audit links supporting evidence. |
| Authorization linkage | Audit links authorization when applicable. |
| Rollback linkage | Audit links rollback when applicable. |

## Required evidence

Audit entry reference and supporting evidence.

## Required audit trail

The audit entry under review must be in `logs/AUDIT_TRAIL.md` or a related
validation log when appropriate.

## Pass criteria

Audit is complete, current, linked and sufficient for the governed action.

## Fail criteria

Audit is missing, stale, ambiguous, unsupported or disconnected from evidence.

## Blocking conditions

Missing or invalid audit blocks closure, merge and release readiness when audit
is required.

## Rollback considerations

Add missing audit, record incident, restore prior audit rule or close PR
without merge.

## Human authorization requirements when applicable

Required when audit supports merge, critical decision, critical rollback,
destructive action or external action.

## Related certification/governance gates

Audit Sufficiency, Evidence Sufficiency, Human Authorization Requirement and
Critical Decision Escalation.

## Minimum checklist

- [ ] Audit requirement named.
- [ ] Evidence linked.
- [ ] Authorization linked when applicable.
- [ ] Rollback linked when applicable.
- [ ] Decision linked when applicable.
- [ ] Staleness checked.
