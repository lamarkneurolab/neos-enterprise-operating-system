# External Execution Boundaries

External Execution Boundaries define what NEOS Block 7 allows, blocks and
requires before any future external execution can be considered.

Block 7 does not execute external connectors or activate external services.

## Boundary classes

| Boundary | Meaning | Default status |
|---|---|---|
| Internal documentation | Markdown changes inside repository. | Allowed with normal repository authorization. |
| Internal runtime contract | SDK or integration contract documentation. | Allowed with evidence and audit when applicable. |
| External read | Read from a connected external system. | Blocked unless explicitly authorized. |
| External write | Modify a connected external system. | Blocked unless explicitly authorized. |
| External side effect | Trigger connector, workflow, notification, job or service. | Blocked in Block 7. |
| Secrets or credentials | Read, store, rotate or administer secrets. | Prohibited in Block 7. |
| Permission change | Change access, roles or scopes. | Prohibited in Block 7. |
| Destructive action | Delete, reset, overwrite or irreversibly mutate. | Prohibited unless separately approved for exact action. |

## Required gate for future external execution

Any future external execution must have:

| Gate | Requirement |
|---|---|
| Authorization | Explicit human approval for the specific external action. |
| Registry references | Capability, permission, tool, connector and runtime registry references. |
| Risk classification | Highest applicable risk level. |
| Task record | Task Queue record with rollback requirement. |
| Event record | Event Bus record for request and result. |
| State validation | State Manager-approved transition. |
| Evidence | Evidence before closure. |
| Audit | Audit for governance-relevant execution. |
| Incident handling | Incident rule for failure, block or degradation. |
| Rollback | Documented rollback or explicit non-rollbackable constraint. |

## Blocked actions in v0.1.0

- Running live connector operations.
- Creating or modifying external services.
- Creating databases.
- Installing dependencies.
- Managing secrets, keys or credentials.
- Changing permissions.
- Creating business agents.
- Deploying production runtime.
- Triggering workflows outside the repository documentation flow.

## Boundary failure rules

| Failure | Required behavior |
|---|---|
| Missing authorization | Stop and record blocked authorization. |
| Missing registry reference | Stop and request registry review. |
| Missing evidence | Block closure and record `missing_evidence` incident. |
| Missing audit | Block closure and record `missing_audit_entry` incident. |
| External execution attempted | Block execution and record boundary incident when applicable. |
| Non-rollbackable action requested | Require explicit approval before execution. |

## Rollback

Block 7 rollback is documentary:

- Revert the Block 7 commit.
- Close the PR without merge.
- Supersede or revoke the contract version.
- Record evidence, audit and incident entries when the boundary failure affected
  runtime governance.
