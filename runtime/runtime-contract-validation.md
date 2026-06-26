# Runtime Contract Validation

## Purpose

Validate that runtime contracts remain documentary, compatible and traceable.

## Scope

SDK, integration contracts, internal interfaces, compatibility matrix,
extension rules, external execution boundaries and versioning rules.

## Related runtime components

`runtime/sdk.md`, `runtime/integration-contracts.md`,
`runtime/internal-interfaces.md`, `runtime/compatibility-matrix.md`,
`runtime/extension-rules.md`, `runtime/external-execution-boundaries.md` and
`runtime/sdk-versioning.md`.

## Validation model

| Scenario | Expected validation |
|---|---|
| SDK contract change | Required fields, version, evidence, audit and rollback are present. |
| Integration contract change | Entry, exit, authorization, evidence, audit, failure and rollback are present. |
| Boundary change | External execution remains blocked unless explicitly authorized. |
| Compatibility change | Compatibility matrix records impact and rollback. |

## Required evidence

Contract diff, compatibility matrix review and related log references.

## Required audit trail

Audit is required for governance-relevant contract, compatibility, boundary or
version changes.

## Pass criteria

Contracts remain compatible with Blocks 1-8 and no execution semantics are
silently expanded.

## Fail criteria

Required contract fields are missing, compatibility is unclear or external
execution is enabled without explicit authorization.

## Blocking conditions

Missing evidence, missing audit, missing rollback, breaking compatibility or
external activation blocks closure and merge.

## Rollback considerations

Restore prior contract text, supersede the contract version, revert the commit
or close the PR without merge.

## Human authorization requirements when applicable

Tiziano authorization is required for breaking compatibility, external action,
critical rollback or merge.

## Related certification/governance gates

SDK Contract Compliance, Integration Contract Compliance, Critical Decision
Escalation, Evidence Sufficiency, Audit Sufficiency and Human Authorization
Requirement.

## Minimum checklist

- [ ] Contract fields present.
- [ ] Compatibility reviewed.
- [ ] Evidence linked.
- [ ] Audit linked.
- [ ] Rollback defined.
- [ ] External execution remains blocked.
