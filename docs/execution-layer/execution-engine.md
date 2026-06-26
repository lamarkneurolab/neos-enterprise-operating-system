# Execution Engine

The Execution Engine is responsible for turning authorized intent into verifiable action.

It executes only after the Authorization Flow has produced an authorized plan.

## Required stages

| Stage | Responsibility | Output |
|---|---|---|
| Intake | Capture request, target, outcome and constraints. | Normalized task record. |
| Intent classification | Identify read, write, commit, push, PR, destructive or external-side-effect intent. | Intent class. |
| Registry consultation | Check capabilities, permissions, tools, connectors and runtimes. | Registry mapping. |
| Risk assessment | Assign the highest applicable risk level. | Risk level and gate. |
| Authorization | Confirm human approval and credential scope when required. | Authorized, blocked or rejected state. |
| Planning | Produce concrete ordered actions and rollback notes. | Execution plan. |
| Execution | Use real tools available in the current runtime. | Tool output and changed artifacts. |
| Verification | Confirm the expected outcome. | Verification result. |
| Evidence logging | Record proof of completion. | Evidence log entry. |
| Audit registration | Record governance-relevant events. | Decision, evidence or audit log update. |
| Rollback registration | Record rollback path or non-rollbackable constraint. | Rollback note. |

## Execution plan

An execution plan must include:

- Files, systems or connectors to be touched.
- Commands or tools to be used.
- Expected outputs.
- Verification command or inspection method.
- Rollback path.
- Known blockers or credential requirements.

## Real tool execution

NEOS must use real available tools in the current runtime. It must not mark work
complete from a plan alone.

Valid execution evidence can include:

- Git status output.
- Git diff summary.
- Commit SHA.
- Push output.
- Pull request URL.
- File paths changed.
- Command verification output.

## Verification

Verification must match the task. Examples:

| Task type | Verification |
|---|---|
| Documentation change | `git diff --check` and file inspection. |
| Commit | `git log --oneline -1` and clean or expected `git status -sb`. |
| Push | Remote push output and upstream branch tracking. |
| Pull request | PR URL or number from GitHub. |
| Workflow change | GitHub accepts push and workflow file is present. |

## Runtime Coordination Layer

After the Authorization Flow produces an authorized plan, runtime work passes
through the Runtime Coordination Layer.

```text
Authorization Flow
  -> Task Queue
  -> Event Bus
  -> State Manager
  -> Runtime Observability
  -> Audit Trail / Incident Records
  -> Runtime Memory / Context Persistence
  -> Execution Snapshots
  -> Execution State Log
  -> Evidence / Audit / Rollback
```

The coordination layer does not replace authorization. It receives authorized
work, records the task state, emits internal events, validates transitions and
preserves auditability.

The Execution Engine must not mark a task as complete unless traceability
exists between:

- The task record in the Task Queue.
- The event record in the Event Bus.
- The state record governed by the State Manager.
- The observability event when the execution is inspected.
- The audit or incident record when required.
- The memory or snapshot record when execution context is persisted or reused.
- The state transition in the Execution State Log.
- The linked evidence or audit record.

Tasks may enter `in_progress` only after valid authorization is linked. Failed
tasks must emit `task.failed`; completed tasks must emit `task.completed`.
Rollback-required tasks must preserve rollback evidence before closure.

## Runtime Observability and Audit Trail

Runtime Observability records, classifies and inspects execution facts. It does
not authorize work, execute actions, retry failed work, mutate state or perform
rollback by itself.

The Execution Engine must preserve links between:

- `runtime/observability.md`
- `runtime/audit-trail.md`
- `runtime/health-signals.md`
- `runtime/incident-records.md`
- `logs/AUDIT_TRAIL.md`
- `logs/INCIDENT_LOG.md`

Medium, high and critical execution events must link evidence. Failed, blocked,
degraded or manual-intervention conditions must link an incident record.
Rollback-related events must link rollback evidence before closure.

## Runtime Memory and Context Persistence

Runtime Memory records the governed context that may be considered for later
review, resume or recovery. Context Persistence records references to validated
runtime facts. Execution Snapshots preserve auditable checkpoints.

The Execution Engine must not resume or recover execution only because memory
exists. Resume or recovery may be considered only when persisted context is
valid, current, authorized, evidenced and auditable.

The Execution Engine must preserve links between:

- `runtime/memory.md`
- `runtime/context-persistence.md`
- `runtime/execution-snapshots.md`
- `runtime/context-resume.md`
- `runtime/state-recovery.md`
- `logs/MEMORY_LOG.md`
- `logs/CONTEXT_SNAPSHOT_LOG.md`

Stale, deprecated, revoked, unaudited or prohibited memory must block resume
until review. Context involving open high or critical incidents must not be
treated as resumable without explicit review.

## Runtime SDK and Integration Contracts

Runtime SDK and Integration Contracts define the documented invocation and
interface surface for future NEOS modules and integrations.

The Execution Engine must treat SDK and integration activity as governed
runtime work. It must preserve links between:

- `runtime/sdk.md`
- `runtime/integration-contracts.md`
- `runtime/internal-interfaces.md`
- `runtime/extension-rules.md`
- `runtime/external-execution-boundaries.md`
- `runtime/sdk-versioning.md`
- `runtime/compatibility-matrix.md`
- `logs/SDK_CONTRACT_LOG.md`
- `logs/INTEGRATION_CONTRACT_LOG.md`

SDK and integration contracts do not authorize work, execute connectors, mutate
state, manage secrets or change permissions by themselves. External execution
is blocked by default unless separately authorized and evidenced.

## Runtime Certification and Governance Gates

Runtime Certification and Governance Gates define the required documentary
checks before runtime work can be closed, promoted, integrated, rolled back,
declared release-candidate-ready or merged.

The Execution Engine must preserve links between:

- `runtime/certification-gates.md`
- `runtime/governance-gate-matrix.md`
- `runtime/pre-merge-governance-review.md`
- `runtime/runtime-compliance-checklist.md`
- `runtime/execution-readiness-certification.md`
- `runtime/integration-readiness-certification.md`
- `runtime/rollback-readiness-certification.md`
- `runtime/evidence-sufficiency-rules.md`
- `runtime/audit-sufficiency-rules.md`
- `runtime/human-authorization-gates.md`
- `runtime/critical-decision-gates.md`
- `runtime/release-candidate-review.md`
- `logs/CERTIFICATION_LOG.md`
- `logs/GOVERNANCE_GATE_LOG.md`
- `logs/RELEASE_CANDIDATE_REVIEW_LOG.md`

The Execution Engine must not mark governed work complete when a required
certification gate is blocked. Missing evidence, missing audit, missing human
authorization, unresolved critical decision, missing rollback readiness or open
high/critical incident blocks closure and merge.

## Runtime Testing and Validation Harness

Runtime Testing and Validation Harness defines the documentary validation
surface used to test runtime flows, contracts, gates, rollback, evidence, audit,
regression and release readiness.

The Execution Engine must preserve links between:

- `runtime/testing-harness.md`
- `runtime/validation-scenarios.md`
- `runtime/test-case-registry.md`
- `runtime/runtime-contract-validation.md`
- `runtime/authorization-flow-validation.md`
- `runtime/execution-flow-validation.md`
- `runtime/task-queue-validation.md`
- `runtime/event-bus-validation.md`
- `runtime/state-manager-validation.md`
- `runtime/observability-validation.md`
- `runtime/audit-trail-validation.md`
- `runtime/memory-context-validation.md`
- `runtime/sdk-contract-validation.md`
- `runtime/integration-contract-validation.md`
- `runtime/certification-gate-validation.md`
- `runtime/governance-gate-validation.md`
- `runtime/rollback-validation.md`
- `runtime/failure-scenario-validation.md`
- `runtime/evidence-validation.md`
- `runtime/audit-validation.md`
- `runtime/regression-validation.md`
- `runtime/release-readiness-validation.md`
- `logs/TEST_CASE_REGISTRY_LOG.md`
- `logs/VALIDATION_LOG.md`
- `logs/TEST_EVIDENCE_LOG.md`
- `logs/REGRESSION_REVIEW_LOG.md`
- `logs/RELEASE_READINESS_VALIDATION_LOG.md`

The harness is documentary in v0.1.0. It must not introduce test runners,
dependencies, CI automation, services, databases or external integrations.

## Runtime Orchestration Readiness and Execution Playbooks

Runtime Orchestration Readiness and Execution Playbooks define the documentary
surface used to decide whether future runtime work may be reviewed for
controlled orchestration.

The Execution Engine must preserve links between:

- `runtime/orchestration-readiness.md`
- `runtime/execution-playbooks.md`
- `runtime/pre-orchestration-checklist.md`
- `runtime/controlled-execution-sequences.md`
- `runtime/operational-runbooks.md`
- `runtime/rollback-playbooks.md`
- `runtime/evidence-collection-playbooks.md`
- `runtime/audit-playbooks.md`
- `runtime/incident-response-playbooks.md`
- `runtime/validation-before-execution-rules.md`
- `runtime/human-authorization-before-orchestration.md`
- `runtime/release-to-orchestration-criteria.md`
- `logs/ORCHESTRATION_READINESS_LOG.md`
- `logs/EXECUTION_PLAYBOOK_LOG.md`
- `logs/INCIDENT_RESPONSE_PLAYBOOK_LOG.md`

Readiness does not authorize execution. Playbooks do not authorize execution.
Orchestration eligibility does not mean orchestration approval. Future
orchestration remains blocked unless validation, evidence, audit, rollback
readiness and required human authorization are complete for the specific scope.

## Runtime Orchestration Dry-Run and Simulation Layer

Runtime Orchestration Dry-Run and Simulation Layer defines the documentary
rehearsal surface required before any future activation can be considered.

The Execution Engine must preserve links between:

- `runtime/orchestration-dry-run.md`
- `runtime/simulation-layer.md`
- `runtime/no-op-execution-model.md`
- `runtime/preflight-checks.md`
- `runtime/dry-run-validation-scenarios.md`
- `runtime/simulated-evidence-collection.md`
- `runtime/simulated-audit-trail.md`
- `runtime/simulated-rollback-flow.md`
- `runtime/incident-simulation.md`
- `runtime/simulation-result-registry.md`
- `runtime/dry-run-pass-fail-criteria.md`
- `runtime/controlled-activation-preconditions.md`
- `runtime/human-authorization-before-activation.md`
- `logs/DRY_RUN_SIMULATION_LOG.md`
- `logs/SIMULATION_RESULT_REGISTRY_LOG.md`
- `logs/PREFLIGHT_CHECK_LOG.md`
- `logs/SIMULATED_ROLLBACK_LOG.md`
- `logs/INCIDENT_SIMULATION_LOG.md`

Before any future activation, the dry-run and simulation layer must be
validated. Dry-run does not execute, simulation does not authorize, no-op does
not modify real state and simulation passed does not mean activation approved.

## Runtime Controlled Activation Gate and Execution Authorization Layer

Runtime Controlled Activation Gate and Execution Authorization Layer defines
the documentary gate required before any future execution can be authorized.

The Execution Engine must preserve links between:

- `runtime/controlled-activation-gate.md`
- `runtime/execution-authorization-layer.md`
- `runtime/activation-request-model.md`
- `runtime/activation-decision-matrix.md`
- `runtime/activation-scope-definition.md`
- `runtime/risk-acceptance-rules.md`
- `runtime/human-approval-workflow.md`
- `runtime/pre-execution-authorization-checklist.md`
- `runtime/activation-evidence-package.md`
- `runtime/activation-audit-requirements.md`
- `runtime/activation-denial-deferral-rules.md`
- `runtime/emergency-stop-abort-conditions.md`
- `runtime/post-authorization-control-rules.md`
- `logs/ACTIVATION_REQUEST_LOG.md`
- `logs/EXECUTION_AUTHORIZATION_LOG.md`
- `logs/RISK_ACCEPTANCE_LOG.md`
- `logs/ACTIVATION_DECISION_LOG.md`
- `logs/EMERGENCY_STOP_ABORT_LOG.md`

Before any future execution, there must be a controlled activation gate,
execution authorization layer, activation evidence package and explicit human
authorization for the exact scope, PR, branch, head SHA, commit and action.
The gate does not execute and authorization does not execute by itself.

## Runtime Controlled Execution Activation Protocol

Runtime Controlled Execution Activation Protocol defines the documentary layer
between a Block 12 authorization decision and any future controlled runtime
execution.

The Execution Engine must preserve links between:

- `runtime/controlled-execution-activation-protocol.md`
- `runtime/activation-session-model.md`
- `runtime/execution-window-definition.md`
- `runtime/go-no-go-decision-protocol.md`
- `runtime/activation-preconditions-verification.md`
- `runtime/runtime-activation-scope-lock.md`
- `runtime/human-final-approval-check.md`
- `runtime/execution-start-conditions.md`
- `runtime/execution-hold-conditions.md`
- `runtime/execution-abort-conditions.md`
- `runtime/evidence-capture-before-activation.md`
- `runtime/audit-record-before-activation.md`
- `runtime/rollback-readiness-before-activation.md`
- `runtime/post-activation-monitoring-preconditions.md`
- `runtime/activation-handoff-rules.md`
- `logs/ACTIVATION_SESSION_LOG.md`
- `logs/GO_NO_GO_DECISION_LOG.md`
- `logs/EXECUTION_WINDOW_LOG.md`
- `logs/ACTIVATION_SCOPE_LOCK_LOG.md`
- `logs/PRE_ACTIVATION_EVIDENCE_LOG.md`

Authorization approved does not execute. Activation protocol does not execute.
Before any future execution, there must be an activation session, execution
window, scope lock, pre-activation evidence, audit record, rollback readiness,
post-activation monitoring preconditions and explicit human go/no-go for the
exact PR, branch, head SHA, commit, scope, action and runtime window.

## Runtime Review Checklist

Before an execution is considered closed, review:

1. Was the task authorized?
2. Was the state transition valid?
3. Was the event recorded?
4. Was evidence created?
5. Was audit recorded?
6. Was there an incident?
7. Was there a rollback?
8. Is the final state coherent?
9. Was the log updated?
10. Was persisted context reviewed before reuse?
11. Was a snapshot created when resume or recovery may be needed?
12. Are memory retention and risk levels documented?
13. Are SDK and integration contract boundaries respected?
14. Is compatibility with Blocks 1-6 preserved?
15. Is external execution blocked unless explicitly authorized?
16. Are required certification gates passed?
17. Is the governance gate matrix outcome documented?
18. Are evidence and audit sufficient?
19. Is human authorization required before merge?
20. Is release candidate review complete when closing a block?
21. Are required validation scenarios and test cases documented?
22. Are regression and release readiness validation complete when applicable?
23. Is orchestration readiness separated from execution authorization?
24. Are playbook, rollback, evidence, audit and incident response references documented?
25. Is human authorization specific to the branch, PR, head SHA and action when applicable?
26. Has dry-run simulation been completed before any future activation request?
27. Are no-op, simulated evidence, simulated audit, simulated rollback and incident simulation records linked?
28. Is activation blocked unless explicit human authorization exists for the exact future scope?
29. Is the controlled activation gate complete before any future execution request?
30. Is the activation evidence package linked to audit, decision and risk records?
31. Is execution authorization scoped to the exact PR, branch, head SHA, commit and action?
32. Is the activation session documented before any future execution window?
33. Is the runtime activation scope locked to the exact PR, branch, head SHA, commit, action and window?
34. Is final human go/no-go recorded before any future controlled execution?

## Evidence and audit

Evidence proves that execution happened. Audit records why execution was allowed
and what governance decision was made.

Evidence belongs in `logs/EVIDENCE_LOG.md`.
Material decisions belong in `logs/DECISION_LOG.md`.
Operational audit events belong in `logs/AUDIT_TRAIL.md` when the action has
runtime significance beyond documentation.
Runtime incidents belong in `logs/INCIDENT_LOG.md`.
Runtime memory belongs in `logs/MEMORY_LOG.md`.
Execution snapshots belong in `logs/CONTEXT_SNAPSHOT_LOG.md`.
Certification outcomes belong in `logs/CERTIFICATION_LOG.md`.
Governance gate outcomes belong in `logs/GOVERNANCE_GATE_LOG.md`.
Release candidate posture belongs in `logs/RELEASE_CANDIDATE_REVIEW_LOG.md`.
Test case registry entries belong in `logs/TEST_CASE_REGISTRY_LOG.md`.
Validation outcomes belong in `logs/VALIDATION_LOG.md`.
Test evidence belongs in `logs/TEST_EVIDENCE_LOG.md`.
Regression reviews belong in `logs/REGRESSION_REVIEW_LOG.md`.
Release readiness validation belongs in
`logs/RELEASE_READINESS_VALIDATION_LOG.md`.
Orchestration readiness reviews belong in
`logs/ORCHESTRATION_READINESS_LOG.md`.
Execution playbook reviews belong in `logs/EXECUTION_PLAYBOOK_LOG.md`.
Incident response playbook reviews belong in
`logs/INCIDENT_RESPONSE_PLAYBOOK_LOG.md`.
Dry-run simulation reviews belong in `logs/DRY_RUN_SIMULATION_LOG.md`.
Simulation results belong in `logs/SIMULATION_RESULT_REGISTRY_LOG.md`.
Preflight checks belong in `logs/PREFLIGHT_CHECK_LOG.md`.
Simulated rollback belongs in `logs/SIMULATED_ROLLBACK_LOG.md`.
Incident simulation belongs in `logs/INCIDENT_SIMULATION_LOG.md`.
Activation requests belong in `logs/ACTIVATION_REQUEST_LOG.md`.
Execution authorization belongs in `logs/EXECUTION_AUTHORIZATION_LOG.md`.
Risk acceptance belongs in `logs/RISK_ACCEPTANCE_LOG.md`.
Activation decisions belong in `logs/ACTIVATION_DECISION_LOG.md`.
Emergency stop and abort reviews belong in
`logs/EMERGENCY_STOP_ABORT_LOG.md`.
Activation sessions belong in `logs/ACTIVATION_SESSION_LOG.md`.
Go/no-go decisions belong in `logs/GO_NO_GO_DECISION_LOG.md`.
Execution windows belong in `logs/EXECUTION_WINDOW_LOG.md`.
Activation scope locks belong in `logs/ACTIVATION_SCOPE_LOCK_LOG.md`.
Pre-activation evidence belongs in `logs/PRE_ACTIVATION_EVIDENCE_LOG.md`.

## Rollback

Every execution plan must declare one of:

| Rollback class | Meaning |
|---|---|
| Revert commit | Use a new commit to reverse repository changes. |
| Restore file | Restore a file from the previous commit or known artifact. |
| Close PR | Close a pull request without merge. |
| Manual remediation | Human action required in an external system. |
| No rollback available | The action is irreversible and must be approved as such before execution. |

## Failure handling

| Failure | Required behavior |
|---|---|
| Missing authorization | Stop and report `blocked_authorization`. |
| Missing credential scope | Stop and report `blocked_credentials`. |
| Missing real tool | Stop and report `blocked_tool_unavailable`. |
| Validation failure | Stop, report failure and do not claim completion. |
| Partial execution | Record completed steps, current state and rollback path. |
| Push rejected | Preserve local commit, report remote error and do not open an empty PR. |
| Missing evidence | Stop closure and record `missing_evidence` incident. |
| Missing audit entry | Stop closure and record `missing_audit_entry` incident. |
| Invalid state transition | Block transition and record `invalid_state_transition` incident. |
| Invalid memory reuse | Block resume and record memory review evidence. |
| Missing snapshot evidence | Block recovery and record missing evidence. |
| Failed certification gate | Block closure, record certification result and remediate or roll back. |
| Missing human authorization | Stop merge or critical action until Tiziano authorizes the specific action. |
| Incomplete release candidate review | Keep PR open and block closure. |
| Failed validation scenario | Block readiness, record validation result and remediate or roll back. |
| Regression failure | Block release readiness and merge until compatibility is restored or explicitly decided. |

## Execution state machine

```text
new
  -> intake
  -> intent_classified
  -> registries_checked
  -> risk_classified
  -> authorization_required
  -> authorized
  -> planned
  -> executing
  -> verifying
  -> evidence_recorded
  -> audit_recorded
  -> closed
```

Failure and blocking states:

```text
authorization_required -> blocked_authorization
authorized -> blocked_tool_unavailable
authorized -> blocked_credentials
executing -> failed_execution
executing -> partial_execution
verifying -> failed_verification
failed_execution -> rollback_required
partial_execution -> rollback_required
rollback_required -> rolled_back
rollback_required -> manual_remediation_required
```
