# Internal Interfaces

Internal Interfaces define allowed documentary boundaries between NEOS runtime
modules.

Each interface must preserve authorization, task, event, state, evidence,
audit, incident, memory and rollback traceability.

## Interface matrix

| Module origin | Module destination | Responsibility | Data permitted | Data prohibited | Event associated | State associated | Evidence associated | Risk | Control |
|---|---|---|---|---|---|---|---|---|---|
| Registry System | Authorization Flow | Provide capability, permission, tool, connector and runtime references. | Registry identifiers and status. | Secrets, tokens, undeclared permissions. | `registry.checked` | `registries_checked` | Registry inspection evidence. | Medium | Block if registry reference is missing. |
| Authorization Flow | SDK Runtime | Allow or block SDK invocation. | Authorization outcome, actor, risk, constraints. | Unapproved credential material. | `sdk.invocation.requested` | `authorized` | Authorization evidence. | High | No invocation without authorization. |
| SDK Runtime | Task Queue | Register SDK or integration work as a task. | `task_id`, contract id, risk, rollback requirement. | Raw secrets or prohibited memory. | `task.created` | `queued` | Task creation evidence. | Medium | Task Queue minimum record required. |
| Task Queue | Event Bus | Emit lifecycle events for SDK and integration tasks. | Task id, event type, state summary. | Full secret payloads or unverified claims. | `task.started`, `task.completed`, `task.failed` | Current task state. | Event linkage evidence. | Medium | Every state transition emits event. |
| Event Bus | State Manager | Request valid state transition review. | Event id, previous state, next state, actor. | Unauthorized transition commands. | `state.transitioned` | Requested next state. | State transition evidence. | High | Invalid transitions blocked. |
| State Manager | Runtime Observability | Make transitions and failures inspectable. | State ids, event ids, severity, risk. | Sensitive payload details. | `runtime.observed` | `in_progress`, `completed`, `failed`, `blocked` | Observability evidence. | Medium | Medium+ events link evidence. |
| Runtime Observability | Audit Trail | Audit governance-relevant runtime facts. | Observability id, task id, evidence ref, incident ref. | Unsupported conclusions. | `audit.logged` | `audit_recorded` | Audit evidence. | Medium | Missing audit creates incident. |
| Audit Trail | Evidence Log | Preserve proof for audited action. | Audit id, evidence id, result summary. | Secret values or unverified external claims. | `evidence.created` | `evidence_recorded` | Evidence entry. | Medium | Evidence must be inspectable. |
| SDK Runtime | Integration Contracts | Validate entry, exit, failure and rollback rules. | Contract id, entry point, exit point, risk. | Live connector credentials. | `integration.entry.requested` | `authorized` | Contract validation evidence. | High | External execution blocked by default. |
| Integration Contracts | External Execution Boundaries | Confirm whether future external execution is allowed. | Boundary classification, authorization requirement. | Real connector execution payloads. | `integration.execution.blocked` | `blocked` or `authorized` | Boundary evidence. | High | No real external execution in v0.1.0. |
| Runtime Memory | SDK Runtime | Provide valid context only after review. | Context id, snapshot id, validation status. | Stale, revoked, secret or unaudited context. | `context.reviewed` | `validated` or `blocked` | Memory review evidence. | High | Stale or revoked context blocks invocation. |
| Context Persistence | State Manager | Link persisted context to state review. | Context id, state id, audit id, evidence id. | Unlinked context or prohibited memory. | `context.persisted` | `validated` | Context evidence. | High | Context requires evidence and audit. |
| Incident Records | State Manager | Block or contain failed states. | Incident id, severity, containment action. | Hidden remediation commands. | `incident.recorded` | `failed`, `blocked`, `rollback_requested` | Incident evidence. | High | High and critical incidents block closure. |
| Rollback Review | Audit Trail | Record rollback request and completion. | Rollback ref, task id, evidence ref. | Destructive unapproved actions. | `task.rollback.requested` | `rollback_requested` | Rollback evidence. | High | Rollback requires evidence before closure. |

## Rules

- Interfaces are documentary contracts, not service calls.
- Interfaces do not authorize work by themselves.
- Interfaces must not carry secrets, credentials, tokens or permission changes.
- Interfaces must not execute external connectors.
- Interfaces must link evidence and audit when state, risk or governance changes.
- Interfaces that cross an external execution boundary are blocked by default in
  v0.1.0.

## Review requirements

Before adding or changing an interface:

1. Confirm the origin and destination modules exist.
2. Confirm allowed and prohibited data.
3. Confirm event and state linkage.
4. Confirm evidence and audit linkage.
5. Confirm risk and rollback handling.
6. Update `runtime/compatibility-matrix.md`.
7. Update SDK or integration logs when applicable.

## Block 8 certification requirement

Internal interface changes must pass the Governance Gate Matrix before closure
or merge. Interface changes that affect allowed data, prohibited data, runtime
boundaries, SDK contracts, integration contracts, rollback or compatibility
must also pass Critical Decision Gates and Rollback Readiness Certification.
