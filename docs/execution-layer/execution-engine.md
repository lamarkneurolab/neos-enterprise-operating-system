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

## Evidence and audit

Evidence proves that execution happened. Audit records why execution was allowed
and what governance decision was made.

Evidence belongs in `logs/EVIDENCE_LOG.md`.
Material decisions belong in `logs/DECISION_LOG.md`.
Operational audit events belong in `logs/AUDIT_TRAIL.md` when the action has
runtime significance beyond documentation.

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
