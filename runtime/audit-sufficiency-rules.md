# Audit Sufficiency Rules

Audit is sufficient when a governance-relevant runtime action can be traced to
its authorization, decision, evidence, incident context and rollback posture.

## Events that require audit

- Block-level documentation baseline creation.
- Certification gate approval, block or rollback-required outcome.
- Governance matrix changes.
- SDK contract changes.
- Integration contract changes.
- External execution boundary changes.
- Memory or context reuse that affects execution readiness.
- Evidence sufficiency decisions.
- Audit sufficiency decisions.
- Human authorization decisions.
- Critical decisions.
- Release candidate review.
- Incident containment, escalation or closure.
- Rollback request, approval or completion.

## Decisions that require traceability

- Merge approval or denial.
- Critical scope change.
- Breaking compatibility change.
- External execution approval.
- Dependency installation approval.
- Permission change approval.
- Secret management approval.
- Destructive action approval.
- Critical rollback approval.
- Release candidate approval.

## Audit log linkage

Required audit entries belong in `logs/AUDIT_TRAIL.md`.

Audit entries should link:

- Runtime component.
- Task ID.
- Event ID.
- Action.
- Authorization reference.
- Decision reference.
- Evidence reference.
- Incident reference.
- Rollback reference.
- Result.
- Risk level.

## Blocking rules

| Omission | Blocks closure | Blocks merge |
|---|---:|---:|
| Missing block-level audit | Yes | Yes |
| Missing audit for required human authorization | Yes | Yes |
| Missing audit for critical decision | Yes | Yes |
| Missing audit for high-risk rollback | Yes | Yes |
| Missing audit for incident affecting closure | Yes | Yes until contained |
| Missing audit for compatibility change | Yes | Yes when compatibility changes |

## Related logs

`logs/DECISION_LOG.md` records material decisions.

`logs/INCIDENT_LOG.md` records missing audit, missing evidence, blocked
authorization, invalid state, boundary violations and unresolved rollback
conditions when they affect closure or merge.
