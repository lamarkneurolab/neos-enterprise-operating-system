# Human Authorization Gates

Human Authorization Gates identify actions that require explicit Tiziano
approval before they can proceed.

## Mandatory human authorization

| Action | Required authorization | Blocking condition | Evidence | Audit | Rollback |
|---|---|---|---|---|---|
| Merge of any PR | Explicit Tiziano authorization for the specific PR. | Missing PR-specific approval or relying on prior PR authorization. | Decision or PR approval reference. | Required before merge. | Do not merge; keep PR open. |
| Dependency installation | Explicit authorization for exact dependency action. | Install attempted without approval. | Command and authorization reference. | Required if attempted or approved. | Revert dependency files or stop. |
| Permission modification | Explicit authorization for exact permission change. | Permission change attempted without approval. | Diff and authorization reference. | Required. | Revert or stop. |
| Secret management | Explicit authorization for exact secret action. | Secret read, storage, rotation or administration attempted without approval. | Authorization reference only; do not log secret values. | Required. | Stop and record incident if attempted. |
| File deletion | Explicit authorization for exact file deletion. | File deletion without approval. | Diff and authorization reference. | Required. | Restore file from prior commit. |
| Destructive change | Explicit authorization for exact destructive action. | Reset, overwrite or irreversible mutation without approval. | Command and authorization reference. | Required. | Restore or revert when possible. |
| Real external integration | Explicit authorization for exact external action. | Connector, service, workflow or side effect activated without approval. | Authorization and execution evidence. | Required. | Stop, contain and rollback only with approval. |
| Business or prohibited agents | Explicit future authorization and separate scope. | Agent created in Block 8. | Not applicable in Block 8; prohibited. | Incident if attempted. | Remove or close PR. |
| Critical scope change | Explicit Tiziano approval. | Scope changes without approval. | Decision log entry. | Required. | Restore approved scope. |
| Release candidate approval | Explicit Tiziano decision. | RC declared approved without Tiziano decision. | RC review log and decision. | Required. | Keep as candidate only. |
| Critical rollback execution | Explicit Tiziano approval. | Critical rollback executed without approval. | Rollback authorization and evidence. | Required. | Stop and escalate. |

## PR #5 authorization boundary

Authorization granted for PR #5 applied only to PR #5. It does not authorize
Block 8, future pull requests, future merges or future destructive actions.

## Block 9 validation linkage

Human authorization gates are validated by
`runtime/authorization-flow-validation.md` and
`runtime/governance-gate-validation.md`.

Validation must confirm that PR #6 authorization applied only to PR #6 and does
not authorize Block 9 or future merges.
