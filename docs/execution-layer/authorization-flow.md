# Authorization Flow

The Authorization Flow is the decision gate that determines whether NEOS may
turn an incoming task into execution.

Authorization is not a general approval feeling. It is a concrete check against
intent, registries, risk, available tools, evidence requirements and rollback.

## Required sequence

1. Intake task.
2. Classify intent.
3. Consult registries.
4. Classify risk.
5. Identify required human authorization.
6. Approve or block execution.
7. Produce an execution plan.
8. Execute only with real tools available in the current runtime.
9. Verify result.
10. Record evidence.
11. Record audit trail.
12. Record rollback path.

## Intake

Every task starts with a request, command or approved plan. Intake must capture:

| Field | Requirement |
|---|---|
| Request | The user-visible task or instruction. |
| Target | Repository, file, connector, runtime or external system affected. |
| Expected outcome | The result that would make the task complete. |
| Constraints | Required branch, files, no-merge rules, no-permission-change rules or other limits. |

## Intent classification

Intent must be classified before execution.

| Intent | Description | Typical authorization |
|---|---|---|
| Read | Inspect files, status, logs or metadata. | Usually allowed in current workspace. |
| Write | Create or update local repository content. | Requires user authorization or active policy. |
| Commit | Stage and commit changes. | Requires explicit task instruction. |
| Push | Publish commits to a remote. | Requires explicit task instruction and credential capability. |
| Pull request | Open a PR against a base branch. | Requires explicit task instruction. |
| Destructive | Delete, reset, overwrite history or remove external records. | Requires explicit approval for the exact action. |
| External side effect | Trigger a connector, remote workflow, publication or notification. | Requires explicit approval and evidence. |

## Registry consultation

Before execution, NEOS must consult the relevant canonical registries:

| Registry | Required check |
|---|---|
| `registries/capability-registry.md` | Does the requested action map to a known capability? |
| `registries/permission-registry.md` | Does the action require human authorization? |
| `registries/tool-registry.md` | Is a real tool available for the action? |
| `registries/connector-registry.md` | Does the action touch an external system? |
| `registries/runtime-registry.md` | Is the active runtime allowed to perform the capability? |

## Risk classification

Risk is classified at the highest applicable level.

| Risk | Criteria | Gate |
|---|---|---|
| Low | Local read-only inspection. | Proceed when workspace access exists. |
| Medium | Local file changes, commits or non-destructive automation. | Proceed with explicit task instruction and verification. |
| High | Pushes, workflow changes, external writes or credential-sensitive operations. | Require explicit human authorization and evidence. |
| Critical | Destructive operations, production changes, financial actions or irreversible external effects. | Require exact-action approval and rollback plan. |

## Human authorization gate

Human authorization is required when the action:

- Writes repository content.
- Commits or pushes changes.
- Opens or updates a pull request.
- Uses a connector with external side effects.
- Changes workflow, credential, permission, billing or production-sensitive files.
- Performs destructive or hard-to-reverse actions.

If authorization is missing, execution must stop in `blocked_authorization`.

## Authorization output

The gate must produce one of three outcomes:

| Outcome | Meaning |
|---|---|
| Authorized | Execution may continue under the documented plan. |
| Blocked | Execution cannot continue until human authorization, credentials or scope are available. |
| Rejected | Execution must not proceed because it violates constraints or governance rules. |
