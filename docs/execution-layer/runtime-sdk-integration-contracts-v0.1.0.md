# Runtime SDK & Integration Contracts v0.1.0

This is the canonical specification for NEOS Fase 3 Block 7.

Block 7 defines the minimum documentary layer for runtime SDK contracts,
internal interfaces, integration contracts, compatibility, extension rules,
external execution boundaries, versioning, traceability, audit, risk, evidence
and rollback.

## Purpose

The purpose of Block 7 is to define how future NEOS modules, SDK consumers,
providers, tools, connectors and agents may integrate with the Execution Layer
without bypassing authorization, state governance, evidence, audit, memory or
rollback requirements.

Block 7 is not a production SDK implementation. It is a contract baseline.

## Scope

Included:

- Runtime SDK contracts.
- Integration contracts.
- Internal interface rules.
- Compatibility matrix.
- Extension rules.
- External execution boundaries.
- SDK versioning rules.
- Risk matrix.
- Review checklist.
- Certification checklist.
- Evidence, audit, incident and rollback linkage.

## Non-goals

Excluded:

- Business agents.
- Commercial, clinical, documentation, marketing, sales or operations agents.
- Production SDK packages.
- External connector execution.
- Databases, workers, queues or services.
- Permission changes.
- Secret management.
- Dependency installation.
- Destructive changes.
- Automatic merge.

## Architecture

```text
Registry System
  -> Authorization Flow
  -> Runtime SDK Contracts
  -> Integration Contracts
  -> Task Queue
  -> Event Bus
  -> State Manager
  -> Runtime Observability
  -> Audit Trail / Incident Records
  -> Runtime Memory / Context Persistence
  -> Evidence / Rollback
```

The SDK and integration layer sits after registry consultation and
authorization. It provides invocation and interface rules but does not execute
work by itself.

## SDK contracts

The canonical SDK contracts are defined in `runtime/sdk.md`.

Minimum contracts:

| Contract | Purpose |
|---|---|
| SDK Runtime Contract | Defines runtime-level invocation rules. |
| SDK Consumer Contract | Defines responsibilities for callers. |
| SDK Provider Contract | Defines responsibilities for runtime modules providing capabilities. |
| SDK Invocation Contract | Defines invocation payload and gate requirements. |
| SDK Response Contract | Defines success and response records. |
| SDK Error Contract | Defines failure and containment records. |
| SDK Evidence Contract | Defines evidence required for contract use. |
| SDK Audit Contract | Defines audit required for contract use. |
| SDK Version Contract | Defines version and compatibility expectations. |

Every SDK contract must include purpose, input, output, precondition,
postcondition, evidence required, audit required, risks, rollback and version.

## Integration contracts

The canonical integration contracts are defined in
`runtime/integration-contracts.md`.

Every integration contract must include entry point, exit point, operational
limits, authorization required, evidence required, audit required, failure rule
and rollback rule.

## Internal interfaces

Internal interfaces are defined in `runtime/internal-interfaces.md`.

Each interface must identify origin module, destination module, responsibility,
allowed data, prohibited data, associated event, associated state, associated
evidence, risk and control.

## Relationship with Authorization

Block 7 inherits Block 3 authorization rules.

SDK calls and integration entry points must not move to execution when:

- Authorization is missing.
- Credential scope is missing.
- Required registry references are missing.
- The request implies external side effects without explicit approval.
- The request is destructive without exact-action approval and rollback.

The expected authorization references remain in
`docs/execution-layer/runtime-authorization-execution-flow-v0.1.0.md` and
`docs/execution-layer/authorization-flow.md`.

`runtime/authorization.md` is not present in the repository at Block 7 creation
time; Block 7 therefore links to the existing authorization documents instead
of inventing a new runtime file.

## Runtime module relationships

| Module | Block 7 relationship |
|---|---|
| Task Queue | SDK and integration work must create or link a task record when runtime state changes. |
| Event Bus | Contract registration, invocation, integration, failure and rollback events must be traceable. |
| State Manager | SDK and integration work must not skip valid state transitions. |
| Observability | Contract and integration activity must be inspectable when it affects runtime governance. |
| Audit Trail | Contract, version, compatibility, boundary and rollback changes must be auditable. |
| Runtime Memory | Contract use may reuse context only when current, evidenced and audited. |
| Context Persistence | Contract-related context must persist references, not secrets or unsupported claims. |
| Evidence Log | Medium, high and critical work must link evidence. |
| Incident Log | Missing evidence, missing audit, invalid state and external boundary violations must be incident-capable. |

## Event extensions

Recommended documentary event types:

- `sdk.contract.registered`
- `sdk.invocation.requested`
- `sdk.invocation.completed`
- `sdk.invocation.failed`
- `integration.contract.registered`
- `integration.entry.requested`
- `integration.exit.completed`
- `integration.execution.blocked`

These event types are documentary extensions and must not introduce a
production event broker.

## Rollback

Repository documentary rollback:

```text
git revert <block_7_commit_sha>
```

Pull request rollback before merge:

```text
Close the Block 7 pull request without merge.
```

Contract-level rollback:

1. Mark the contract version as superseded or revoked.
2. Restore the prior compatible contract reference.
3. Record decision, evidence, audit and incident entries when required.
4. Verify compatibility matrix and rollback links.

## Risk matrix

| Risk | Scenario | Impact | Control | Rollback |
|---|---|---|---|---|
| Missing authorization | SDK invocation proceeds without approval. | Unauthorized execution path. | Authorization gate inherited from Block 3. | Block invocation; record incident. |
| Contract drift | SDK contract no longer matches runtime modules. | Integration ambiguity. | Compatibility matrix and version log. | Restore previous contract version. |
| Evidence gap | Contract use has no evidence. | Closure cannot be trusted. | Evidence contract and evidence log. | Block closure; record incident. |
| Audit gap | Governance action lacks audit. | Review trail incomplete. | Audit contract and audit trail. | Record missing audit incident. |
| External side effect | Future integration executes real connector. | Unauthorized external change. | External execution boundaries. | Stop execution; rollback only if approved and documented. |
| Memory misuse | Contract reuses stale or prohibited context. | Incorrect execution context. | Block 6 memory review. | Mark context stale, deprecated or revoked. |
| Version incompatibility | New contract breaks a module. | Runtime contract failure. | Semantic version and compatibility matrix. | Revert contract or create compatible minor version. |

## Review checklist

- [ ] Markdown source only.
- [ ] No dependencies added.
- [ ] No permissions changed.
- [ ] No secrets managed.
- [ ] No business agents created.
- [ ] No external integrations executed.
- [ ] No files deleted.
- [ ] SDK contracts include all required fields.
- [ ] Integration contracts include all required fields.
- [ ] Internal interfaces include all required fields.
- [ ] Compatibility matrix updated.
- [ ] Risks and rollback documented.
- [ ] Evidence, audit, state and incident logs updated when applicable.
- [ ] PR remains unmerged pending review and explicit authorization.

## Certification checklist

- [ ] Block 7 links to Blocks 1-6 without replacing them.
- [ ] Runtime SDK rules preserve Authorization, Task Queue, Event Bus, State
  Manager, Observability, Audit Trail, Memory and Context Persistence.
- [ ] External execution boundaries block real connector execution by default.
- [ ] Versioning rules define backward compatibility and breaking changes.
- [ ] Traceability exists from contract to task, event, state, evidence, audit,
  incident and rollback.
- [ ] Working tree is clean after commit and push.
- [ ] Pull request is open for review.
- [ ] No merge has been executed.

## v0.1.0 status

Status: documentary baseline for review.

Canonical source: GitHub.

Official source format: Markdown.

## Block 8 certification linkage

Block 8 adds certification and governance gates over SDK and integration
contracts without changing the Block 7 contract baseline.

SDK and integration changes must pass:

- `runtime/certification-gates.md`
- `runtime/governance-gate-matrix.md`
- `runtime/integration-readiness-certification.md`
- `runtime/evidence-sufficiency-rules.md`
- `runtime/audit-sufficiency-rules.md`
- `runtime/human-authorization-gates.md`
- `runtime/critical-decision-gates.md`

Breaking compatibility, external boundary changes, live integration activation
or missing rollback readiness blocks merge until the required decision,
evidence, audit and authorization are documented.
