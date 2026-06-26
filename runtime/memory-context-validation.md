# Memory & Context Validation

## Purpose

Validate runtime memory and context persistence before reuse, resume, recovery
or release readiness.

## Scope

Memory creation, context persistence, context resume, snapshot validation,
memory boundary enforcement, invalid context rejection, context contamination
prevention, retention rules and memory audit linkage.

## Related runtime components

Runtime Memory, Context Persistence, Execution Snapshots, Context Resume,
State Recovery, Memory Log and Context Snapshot Log.

## Validation model

| Scenario | Expected validation |
|---|---|
| Memory creation | Context has ID, origin, risk and retention rule. |
| Context persistence | Persisted context links task, event, state, evidence and audit. |
| Context resume | Resume uses current, valid and authorized context. |
| Snapshot validation | Snapshot is linked and inspectable. |
| Boundary enforcement | Secrets, credentials and prohibited context are excluded. |
| Invalid context rejection | Stale, revoked or contaminated context blocks reuse. |
| Retention rules | Context lifetime is defined. |
| Audit linkage | Memory affecting decisions links audit. |

## Required evidence

Memory/context record, snapshot reference, validation result and evidence link.

## Required audit trail

Audit is required for context reuse, resume, recovery, high/critical memory and
memory affecting decisions or rollback.

## Pass criteria

Context is current, valid, evidenced, audited when required and not prohibited.

## Fail criteria

Context is stale, revoked, contaminated, unaudited, unsupported or prohibited.

## Blocking conditions

Invalid or unaudited context blocks resume, recovery, closure, merge and
release readiness.

## Rollback considerations

Revoke context, mark stale/deprecated, restore prior context rule or close PR
without merge.

## Human authorization requirements when applicable

Required for restricted context, high/critical reuse, critical recovery,
critical rollback or merge.

## Related certification/governance gates

Memory Safety, Evidence Sufficiency, Audit Sufficiency, Rollback Readiness and
Human Authorization Requirement.

## Minimum checklist

- [ ] Context ID exists.
- [ ] Risk assigned.
- [ ] Retention rule declared.
- [ ] Evidence linked.
- [ ] Audit linked when required.
- [ ] Stale/revoked status checked.
