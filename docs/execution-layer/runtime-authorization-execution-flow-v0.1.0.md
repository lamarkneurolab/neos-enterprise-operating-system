# Runtime Authorization & Execution Flow v0.1.0

This is the canonical specification for NEOS Block 3.

Block 3 defines how NEOS receives work, authorizes it, executes it with real
available tools, verifies the result and records evidence.

## Scope

Included:

- Task intake.
- Intent classification.
- Registry consultation.
- Risk classification.
- Human authorization gates.
- Execution planning.
- Tool-backed execution.
- Verification.
- Evidence.
- Audit.
- Rollback.
- Failure handling.
- Execution state machine.

Excluded:

- Creating business agents.
- Modifying permissions.
- Automatic merge.
- Opening empty pull requests.

## 1. Task intake

The runtime must capture the incoming task as an execution candidate.

| Intake field | Description |
|---|---|
| Request | User instruction or approved plan. |
| Branch | Required branch or branch constraint. |
| Targets | Files, directories, connectors or systems affected. |
| Desired result | Observable completion criteria. |
| Constraints | No-merge, no-permission-change, no-delete or other limits. |
| Required report | Outputs the user explicitly requested. |

If the task lacks enough information to avoid unsafe action, the runtime must
ask for clarification or stop with a blocker.

## 2. Intent classification

The runtime classifies intent before consulting authorization gates.

| Intent class | Examples | Default risk |
|---|---|---|
| Read | Inspect files, branch, logs or registry records. | Low |
| Local write | Update documentation or code locally. | Medium |
| Commit | Stage and commit selected files. | Medium |
| Push | Push a local branch to remote. | High |
| Pull request | Create a PR against `main`. | High |
| External execution | Trigger connector, workflow or remote side effect. | High |
| Destructive | Delete files, reset history, remove records. | Critical |

## 3. Registry consultation

The runtime must consult registries according to the action:

| Question | Registry |
|---|---|
| What capability is being used? | `registries/capability-registry.md` |
| What permission is required? | `registries/permission-registry.md` |
| What real tool can perform the work? | `registries/tool-registry.md` |
| Is an external system involved? | `registries/connector-registry.md` |
| Is the runtime allowed to execute it? | `registries/runtime-registry.md` |

Registry consultation does not modify permissions.

## 4. Risk classification

Risk is assigned using the highest matching category:

| Risk | Definition | Required gate |
|---|---|---|
| Low | Read-only local inspection. | Workspace access. |
| Medium | Local change, local validation or commit. | Explicit instruction and verification. |
| High | Push, PR, workflow update or external write. | Human authorization and credential scope. |
| Critical | Destructive or irreversible action. | Exact-action approval and rollback plan. |

## 5. Human authorization

Human authorization is required for:

- Repository writes.
- Commits.
- Pushes.
- Pull requests.
- External side effects.
- Destructive operations.
- Workflow changes.
- Credential, billing, production or permission changes.

If authorization or credential scope is missing, the runtime must not simulate
success. It must report the blocker and preserve local state when possible.

## 6. Execution plan

The plan must be concrete and ordered.

Required fields:

| Field | Requirement |
|---|---|
| Steps | Ordered actions to perform. |
| Tools | Real tools that will execute each step. |
| Files | Exact files or directories expected to change. |
| Verification | Commands or inspections proving success. |
| Evidence | Logs, commit hash, PR URL or output to record. |
| Rollback | How to reverse or remediate the action. |

## 7. Execution with real tools

Execution must use available runtime tools such as file edits, shell commands,
Git, GitHub connector capabilities or other approved connectors.

NEOS must not:

- Claim completion without performing the action.
- Open a PR when there is no diff.
- Merge automatically.
- Modify permissions as part of Block 3.
- Create business agents.

## 8. Verification

Verification must happen after execution and before final reporting.

Minimum verification for documentation-only repository work:

```text
git status -sb
git diff --check
```

Additional verification may include file inspection, commit inspection, push
output and PR URL capture.

## 9. Evidence

Evidence is recorded in `logs/EVIDENCE_LOG.md`.

Evidence must identify:

- Date.
- Evidence ID.
- Action.
- Result.
- Verification method.

For Block 3 v0.1.0, the evidence record must mention the documentation package,
commit and validation commands.

## 10. Audit

Auditability requires preserving:

- User instruction.
- Branch used.
- Files changed.
- Validation output.
- Commit SHA.
- Push result.
- Pull request result, if created.
- Blockers, if any.

Material governance decisions are recorded in `logs/DECISION_LOG.md`.

## 11. Rollback

Rollback must be documented before execution.

For repository documentation changes, the preferred rollback is:

```text
git revert <commit_sha>
```

If push succeeds but PR is not merged, rollback may also be:

```text
git revert <commit_sha>
git push
```

If PR creation succeeds but the change should not proceed, close the PR without
merge.

## 12. Failure handling

| Failure condition | Runtime response |
|---|---|
| No diff exists | Do not commit and do not open PR. |
| Authorization missing | Stop and report blocker. |
| Credential scope missing | Preserve local commit and report remote rejection. |
| Tool unavailable | Stop and identify missing tool. |
| Verification fails | Do not claim completion; report failure and current state. |
| Push fails | Keep local branch and commit; report exact push error. |
| PR creation fails | Report error and provide branch/commit details. |

## 13. State machine

```text
new
  -> intake_captured
  -> intent_classified
  -> registries_consulted
  -> risk_classified
  -> authorization_checked
  -> plan_created
  -> executing
  -> verifying
  -> evidence_logged
  -> audit_ready
  -> pushed
  -> pr_opened
  -> closed
```

Blocking and failure transitions:

```text
authorization_checked -> blocked_authorization
authorization_checked -> blocked_credentials
plan_created -> blocked_tool_unavailable
executing -> failed_execution
executing -> partial_execution
verifying -> failed_verification
pushed -> blocked_pr_creation
failed_execution -> rollback_required
partial_execution -> rollback_required
rollback_required -> rolled_back
rollback_required -> manual_remediation_required
```

## 14. Completion criteria

Block 3 v0.1.0 is complete when:

1. The required documents exist.
2. Existing partial documents are expanded instead of duplicated.
3. Decision and evidence logs are updated.
4. `git status -sb` and `git diff --check` are executed.
5. A non-empty commit is created.
6. Push is attempted and reported.
7. A PR is opened only if the branch contains a real diff against `main`.
