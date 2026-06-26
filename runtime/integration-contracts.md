# Integration Contracts

Integration Contracts define the minimum documentary rules for internal and
future external integration points in NEOS.

The v0.1.0 integration layer does not execute connectors, activate services or
create production integrations.

## Integration contract template

Every integration contract must include entry point, exit point, operational
limits, authorization required, evidence required, audit required, failure rule
and rollback rule.

## Contracts

| Contract | Entry point | Exit point | Operational limits | Authorization required | Evidence required | Audit required | Failure rule | Rollback rule |
|---|---|---|---|---|---|---|---|---|
| Integration Contract | Authorized runtime task with registry and SDK contract references. | Completed, blocked, failed or rollback-required state. | Documentation-only in v0.1.0; no real connector execution. | Block 3 authorization for repository, PR, external or destructive actions. | Evidence log entry for medium, high and critical integration changes. | Audit Trail entry for governance-relevant integration changes. | Enter `failed` or `blocked`, emit event and record incident when required. | Revert documentation commit, restore prior contract or close PR without merge. |
| Integration Entry Point | `integration.entry.requested` event linked to an authorized task. | Entry accepted, blocked or rejected. | Validate capability, permission, connector and runtime registry references. | Explicit approval for external side effects or high-risk execution. | Entry validation evidence. | Required when entry enables new contract surface or external boundary. | Block entry when authorization, evidence, audit or registry references are missing. | Remove or supersede the entry contract and log rollback evidence. |
| Integration Exit Point | Accepted integration entry or SDK invocation. | `completed`, `blocked`, `failed`, `cancelled` or `rolled_back`. | Must not claim completion without verification and evidence. | Same authorization scope as the entry point. | Exit result evidence and verification method. | Required for high-risk completion, failure or rollback. | If verification fails, exit as `failed` and preserve current state. | Trigger rollback evaluation and link rollback reference before closure. |
| Integration Precondition | Before integration entry is accepted. | Precondition satisfied or blocked. | Requires authorized task, valid state, registry references and risk classification. | Required before any execution or external boundary is crossed. | Precondition inspection evidence for medium, high and critical work. | Required when precondition approval changes governance posture. | Missing precondition blocks execution and records incident when closure is affected. | No runtime side effect may exist; rollback is contract correction or PR closure. |
| Integration Postcondition | After integration action or documentary update completes. | Verified state with evidence and audit links. | Preserve task, event, state, evidence, audit and rollback traceability. | Must match the authorization that allowed execution. | Result verification evidence. | Required for governance-relevant outcomes. | Missing postcondition prevents closure and records incident when required. | Restore prior state or mark contract version superseded. |
| Integration Evidence Requirement | Any medium, high or critical integration contract use. | Evidence reference accepted or missing evidence incident. | Evidence is a reference to verifiable runtime facts, not an unsupported claim. | Required when evidence supports authorized execution. | `logs/EVIDENCE_LOG.md` entry. | Required when evidence supports governance decisions. | Missing evidence blocks closure. | Record `missing_evidence` incident and restore prior compatible contract if needed. |
| Integration Audit Requirement | Any governance-relevant integration contract use. | Audit reference accepted or missing audit incident. | Audit records decision, evidence, authorization and rollback context. | Required for audited execution or boundary change. | Evidence supporting the audit entry. | `logs/AUDIT_TRAIL.md` entry. | Missing audit blocks closure for required audit actions. | Record `missing_audit_entry` incident and remediate before closure. |
| Integration Failure Rule | Failed, blocked, degraded or invalid integration condition. | Incident, failed state or rollback-required state. | Preserve partial execution state and do not retry autonomously. | Required for remediation that changes files, state or external systems. | Failure evidence and current state. | Required for high-risk or governance-relevant failure. | Emit failure event, enter valid failed state and link incident when required. | Evaluate rollback before closure and preserve rollback evidence. |
| Integration Rollback Rule | Rollback requested by failure, review or human instruction. | Rolled back, failed rollback or closed without merge. | Rollback must be documented and verified. | Required for repository writes, external remediation or destructive rollback. | Rollback evidence and verification output. | Required for rollback request and completion. | Rollback failure records incident and blocks closure. | Prefer `git revert <commit_sha>` for repository documentation changes. |

## Non-goals

- No connector is executed.
- No external system is modified.
- No database or service is created.
- No business agent integration is created.

## Block 8 certification requirement

Integration contract changes must pass the following Block 8 gates before
closure or merge:

- Integration Readiness.
- Integration Contract Compliance.
- Evidence Sufficiency.
- Audit Sufficiency.
- Rollback Readiness.
- Human Authorization Requirement before merge or any external action.
- Critical Decision Escalation when boundaries, data rules, compatibility or
  rollback posture change.

Required logs:

- `logs/INTEGRATION_CONTRACT_LOG.md`
- `logs/CERTIFICATION_LOG.md`
- `logs/GOVERNANCE_GATE_LOG.md`
- `logs/EVIDENCE_LOG.md`
- `logs/AUDIT_TRAIL.md`

Real external execution remains blocked by default. Any live connector,
service, workflow, notification, job or external side effect requires explicit
Tiziano authorization for the exact action.
