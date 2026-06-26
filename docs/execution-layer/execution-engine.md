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
