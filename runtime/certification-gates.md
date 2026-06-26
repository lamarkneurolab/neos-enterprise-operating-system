# Certification Gates

Certification Gates define the minimum runtime governance checks required
before work can close, promote, integrate, merge, roll back or become a release
candidate.

## Gate catalog

| Gate | Purpose | Entry condition | Approval condition | Blocking condition | Minimum evidence | Minimum audit | Risk | Rollback | Reviewer | Timing | Logs |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Execution Readiness | Confirm a runtime execution flow is ready. | Execution flow is proposed or changed. | Authorized input, state, task, event, evidence, audit, rollback and closure criteria exist. | Missing authorization, state, task, event, evidence, audit or rollback. | Execution plan, file list, validation command and expected outcome. | Audit entry when execution affects runtime governance. | Unsafe execution closure. | Block execution or close PR without merge. | Runtime governance reviewer. | Before execution or closure. | `EVIDENCE_LOG.md`, `AUDIT_TRAIL.md`, `EXECUTION_STATE_LOG.md`, `CERTIFICATION_LOG.md` |
| Integration Readiness | Confirm an integration contract is ready without activating integration. | Integration contract, SDK boundary or external boundary changes. | Contract, boundary, allowed data, prohibited data, evidence, audit, rollback and authorization are documented. | Real external execution, missing contract, missing boundary or missing authorization. | Contract inspection and compatibility evidence. | Audit entry for integration or boundary changes. | Unauthorized integration. | Supersede contract, revert commit or close PR. | Integration governance reviewer. | Before integration claim or merge. | `EVIDENCE_LOG.md`, `AUDIT_TRAIL.md`, `INTEGRATION_CONTRACT_LOG.md`, `CERTIFICATION_LOG.md` |
| Rollback Readiness | Confirm failure can be reversed or contained. | Any medium, high or critical runtime change. | Rollback condition, scope, files, logs, prior state, evidence, risk and owner are documented. | Rollback unavailable without explicit approval or undocumented containment. | Rollback path and verification method. | Audit entry for high or critical rollback posture. | Unrecoverable failure. | Define rollback before closure; close PR if unresolved. | Runtime governance reviewer or Tiziano for critical rollback. | Before closure and release candidate review. | `CERTIFICATION_LOG.md`, `GOVERNANCE_GATE_LOG.md`, `INCIDENT_LOG.md` |
| Evidence Sufficiency | Confirm evidence is verifiable and enough. | Evidence is used to support closure, merge, decision or certification. | Evidence is specific, current, linked and reproducible or inspectable. | Evidence is missing, ambiguous, stale, fabricated or unsupported. | Evidence log entry with verification method. | Audit when evidence supports governance decision. | False closure. | Block closure and record incident. | Reviewer of the governed action. | Before certification, closure or merge. | `EVIDENCE_LOG.md`, `CERTIFICATION_LOG.md`, `INCIDENT_LOG.md` |
| Audit Sufficiency | Confirm audit trace is complete. | Governance-relevant runtime action or decision occurs. | Audit links action, authorization, decision, evidence, incident and rollback context when applicable. | Missing audit for required event or decision. | Evidence supporting audit. | Audit entry in `logs/AUDIT_TRAIL.md`. | Incomplete accountability. | Block merge and remediate audit. | Runtime governance reviewer. | Before closure or merge. | `AUDIT_TRAIL.md`, `DECISION_LOG.md`, `INCIDENT_LOG.md` |
| Memory Safety | Confirm persisted or reused context is valid. | Runtime memory or context persistence is created, reused or changed. | Context is current, allowed, evidenced, audited and not stale, revoked or prohibited. | Stale, revoked, unaudited or prohibited context. | Memory/context inspection and evidence link. | Audit for governance-relevant memory reuse. | Invalid context reuse. | Revoke context reference or block resume. | Memory governance reviewer. | Before resume, recovery or closure. | `MEMORY_LOG.md`, `CONTEXT_SNAPSHOT_LOG.md`, `CERTIFICATION_LOG.md` |
| SDK Contract Compliance | Confirm SDK contract changes remain compatible. | SDK contract or version changes. | Required SDK fields, compatibility, evidence, audit and rollback are documented. | Missing contract field, breaking drift or contradiction with Block 7. | SDK contract inspection and compatibility evidence. | Audit for contract changes. | Contract drift. | Restore prior contract or supersede version. | SDK governance reviewer. | Before merge. | `SDK_CONTRACT_LOG.md`, `GOVERNANCE_GATE_LOG.md` |
| Integration Contract Compliance | Confirm integration rules remain safe. | Integration contract or external boundary changes. | Contract includes required fields and blocks real external execution by default. | Missing boundary, missing authorization or live integration activation. | Integration contract inspection. | Audit for boundary changes. | External side effect. | Revert or close PR. | Integration governance reviewer. | Before merge. | `INTEGRATION_CONTRACT_LOG.md`, `GOVERNANCE_GATE_LOG.md` |
| Release Candidate Readiness | Confirm a block may become a release candidate. | Block scope is complete and PR is ready for review. | Scope, files, validation, traceability, logs, evidence, audit, rollback, restrictions and risks are documented. | Missing required review item or missing human decision. | Release candidate review entry. | Audit trail for release candidate posture. | Premature closure. | Keep PR open; remediate gaps. | ChatGPT reviewer and Tiziano decision owner. | Before declaring release candidate. | `RELEASE_CANDIDATE_REVIEW_LOG.md`, `CERTIFICATION_LOG.md` |
| Human Authorization Requirement | Confirm human authorization is required and obtained. | Merge, dependency, permission, secret, deletion, destructive, external, agent, critical scope, RC or critical rollback action. | Explicit Tiziano authorization for the specific action exists. | Missing specific authorization or relying on prior PR authorization. | Authorization reference in decision or audit log. | Audit entry for governance-relevant authorization. | Unauthorized action. | Stop action; no merge; no external side effect. | Tiziano. | Before action. | `DECISION_LOG.md`, `AUDIT_TRAIL.md`, `GOVERNANCE_GATE_LOG.md` |
| Critical Decision Escalation | Confirm critical decisions are identified and escalated. | Architecture, boundary, contract, authorization, memory, evidence, audit, compatibility, rollback or external execution changes. | Decision is logged, risk-classified, evidenced and authorized when required. | Critical decision not logged or not authorized. | Decision evidence and risk context. | Audit entry linking decision. | Unreviewed critical change. | Block merge or rollback change. | Tiziano for critical approval. | Before merge or release candidate. | `DECISION_LOG.md`, `AUDIT_TRAIL.md`, `GOVERNANCE_GATE_LOG.md` |

## Blocking rule

Any required gate that fails blocks the governed outcome. Allowed outcomes are:

- Remediate and re-run the gate.
- Record an incident and keep the PR open.
- Close the PR without merge.
- Revert or supersede the affected documentary change.
- Execute approved rollback when explicitly authorized.

No gate failure may be ignored to declare closure.

## Block 9 validation linkage

Certification gates are validated by `runtime/certification-gate-validation.md`
and related Block 9 validation files. Required certification outcomes should
link test cases, validation scenarios, evidence, audit, rollback posture and
release readiness validation when a block is prepared for closure.
