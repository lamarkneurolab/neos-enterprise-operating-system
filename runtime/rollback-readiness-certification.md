# Rollback Readiness Certification

Rollback Readiness Certification determines whether a runtime or documentation
change can be reversed, contained or safely left unmerged.

## Required rollback record

| Field | Requirement |
|---|---|
| Rollback condition | The failure, review finding or human instruction that triggers rollback. |
| Rollback scope | Files, logs, contracts, state references or external boundaries affected. |
| Affected files | Explicit file list or PR diff reference. |
| Affected logs | Logs that must be updated during rollback. |
| Previous state | Known prior state, commit, contract version or documented baseline. |
| Reversibility evidence | Evidence that rollback path is available or why it is not. |
| Residual risk | Risk remaining after rollback or containment. |
| Authorization owner | Reviewer or Tiziano when rollback is critical. |
| Closure criterion | How rollback completion is verified. |

## Rollback classes

| Class | Use | Evidence | Audit | Human authorization |
|---|---|---|---|---|
| Close PR | Work is not merged. | PR status or URL. | Required for governance-relevant PR closure. | Required if closure follows critical decision. |
| Revert commit | Merged documentation must be reversed. | Revert commit SHA and diff. | Required. | Required for critical rollback. |
| Restore file | File content returns to known baseline. | File diff and validation output. | Required when governance-relevant. | Required when destructive or critical. |
| Supersede contract | Contract version remains historically visible but is replaced. | Contract log and compatibility update. | Required. | Required for breaking or critical changes. |
| Revoke context | Memory/context reference is unsafe. | Memory log and incident link. | Required. | Required for high/critical recovery. |
| Manual remediation | Human action outside repository is required. | Human decision and result evidence. | Required. | Always required. |

## Blocking rule

If rollback readiness is missing for medium, high or critical work, closure and
merge are blocked. If rollback is impossible, that fact must be explicitly
documented and approved before any irreversible action is attempted.
