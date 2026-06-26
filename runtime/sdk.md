# Runtime SDK Contracts

The Runtime SDK contracts define the minimum documentary surface for future
NEOS SDK consumers and providers.

The v0.1.0 SDK is a contract layer only. It is not a package, service, worker,
connector, database or external execution runtime.

## Contract record template

Every SDK contract must include:

| Field | Requirement |
|---|---|
| Purpose | Why the contract exists. |
| Input | Allowed input fields or references. |
| Output | Expected output fields or references. |
| Precondition | Required state before use. |
| Postcondition | Required state after use. |
| Evidence required | Evidence that must be linked. |
| Audit required | Audit record that must be linked. |
| Risks | Known failure or misuse scenarios. |
| Rollback | How to reverse, contain or supersede the contract use. |
| Version | Contract version. |

## SDK contracts

| Contract | Purpose | Input | Output | Precondition | Postcondition | Evidence required | Audit required | Risks | Rollback | Version |
|---|---|---|---|---|---|---|---|---|---|---|
| SDK Runtime Contract | Govern all SDK interactions. | Authorized task reference, registry references, payload summary, risk level. | Accepted, blocked or failed runtime result. | Authorization and registry consultation are complete. | Task, event, state, evidence and audit links are created or updated when applicable. | Evidence log entry for medium, high and critical use. | Audit Trail entry for governance-relevant SDK use. | Unauthorized invocation, missing registry scope, missing evidence, state bypass. | Block invocation, restore prior contract version or revert repository commit. | `0.1.0` |
| SDK Consumer Contract | Define caller responsibilities. | Consumer identity, requested capability, task reference, expected result, constraints. | Validated, blocked or rejected request. | Consumer has an approved task and capability reference. | Consumer action is traceable to task, event, state, evidence and audit. | Request evidence and validation result. | Required when consumer action changes runtime state or contract version. | Caller bypasses authorization, passes prohibited data or triggers external execution. | Reject request, revoke context reference or revert contract change. | `0.1.0` |
| SDK Provider Contract | Define module responsibilities for exposed capabilities. | Provider module, capability reference, supported version, operational limits. | Provider acceptance, compatibility status or blocked status. | Provider capability is documented and compatible with runtime boundaries. | Provider response is versioned and linked to evidence when used. | Compatibility evidence and provider contract reference. | Required for new providers, version changes or high-risk capabilities. | Provider drift, unsupported version, capability overreach, hidden side effects. | Disable provider reference, restore previous compatible version or revert commit. | `0.1.0` |
| SDK Invocation Contract | Define the minimum invocation request. | `invocation_id`, `task_id`, `contract_id`, `actor`, `capability_ref`, `permission_ref`, `payload_summary`, `risk_level`. | Invocation accepted, blocked, failed or completed record. | Task is authorized and transition to `in_progress` is allowed. | Event Bus and State Manager records reflect the invocation outcome. | Invocation evidence for medium, high and critical work. | Required when invocation changes runtime state or governance posture. | Invalid state transition, missing permission reference, external execution attempt. | Emit failure or rollback event, block closure and record incident when required. | `0.1.0` |
| SDK Response Contract | Define successful or blocked SDK response. | Invocation record and provider result. | `response_id`, `invocation_id`, `status`, `result_summary`, `evidence_ref`, `audit_ref`, `rollback_ref`. | Invocation exists and provider result is available. | Response is linked to evidence and state transition. | Response evidence for completion or blocking. | Required for high-risk, blocked or governance-relevant responses. | Response claims success without evidence, output includes prohibited data. | Mark response invalid, restore previous state reference and record incident if needed. | `0.1.0` |
| SDK Error Contract | Define failures and containment. | Failed invocation, error type, affected module, evidence status, rollback status. | Error record, incident reference and next allowed state. | Invocation or provider response failed, blocked or degraded. | Failure is inspectable through Event Bus, Observability, Audit Trail and Incident Log. | Failure evidence and command or inspection output when available. | Required for missing evidence, missing audit, invalid state or external boundary violations. | Silent failure, incomplete rollback, repeated invalid invocation. | Enter `failed`, request rollback when needed and preserve containment evidence. | `0.1.0` |
| SDK Evidence Contract | Define evidence requirements for SDK use. | Contract id, invocation id, task id, verification method, result. | Evidence reference in `logs/EVIDENCE_LOG.md`. | SDK use changes documentation, state, contract, version or integration boundary. | Evidence can be linked from task, event, state, audit and rollback records. | Evidence entry for qualifying actions. | Required when evidence supports governance-relevant action. | Missing evidence prevents reliable closure. | Block closure and record `missing_evidence` incident. | `0.1.0` |
| SDK Audit Contract | Define audit requirements for SDK use. | Contract id, task id, event id, authorization reference, decision reference, evidence reference. | Audit reference in `logs/AUDIT_TRAIL.md`. | SDK use affects runtime governance, compatibility, external boundaries or rollback. | Audit can be reviewed with linked decision and evidence. | Evidence supporting the audited action. | Audit entry for qualifying actions. | Missing audit creates incomplete governance trail. | Record `missing_audit_entry` incident and block closure until remediated. | `0.1.0` |
| SDK Version Contract | Define versioning and compatibility expectations. | Contract id, current version, proposed version, compatibility status, migration notes. | Version decision, compatibility record and rollback rule. | Proposed version change has review evidence. | Compatibility matrix and logs are updated. | Version change evidence and compatibility inspection. | Required for minor, major or breaking changes. | Breaking module compatibility or undocumented contract drift. | Restore prior version, mark new version superseded or revert commit. | `0.1.0` |

## Non-goals

- No SDK package is published.
- No connectors are executed.
- No business agents are created.
- No secrets, credentials or permissions are stored.

## Block 8 certification requirement

SDK contract changes must pass the following Block 8 gates before closure or
merge:

- SDK Contract Compliance.
- Evidence Sufficiency.
- Audit Sufficiency.
- Rollback Readiness.
- Critical Decision Escalation when compatibility, authorization or external
  boundary semantics change.
- Human Authorization Requirement before merge.

Required logs:

- `logs/SDK_CONTRACT_LOG.md`
- `logs/CERTIFICATION_LOG.md`
- `logs/GOVERNANCE_GATE_LOG.md`
- `logs/EVIDENCE_LOG.md`
- `logs/AUDIT_TRAIL.md`

If evidence, audit, authorization or rollback readiness is missing, the SDK
contract change remains blocked.
