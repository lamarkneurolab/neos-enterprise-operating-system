# Blocked Action Map

## Purpose

This map lists actions NEOS/NEXUS must block unless exact authorization and required evidence are present. Some actions remain blocked when prohibited by the active operating boundary.

## Block Map

| Action | Block condition |
| --- | --- |
| Merge or auto-merge | Missing PR number, exact Head SHA, base branch, or explicit merge approval. |
| Force push or destructive reset | No explicit destructive-action authorization. |
| Permission mutation | Missing current state, target state, affected principals, authorization, or rollback. |
| Secrets or credentials | Any request to expose, log, copy, or document secret values. |
| Production mutation | Missing environment, service, rollback, health check, or change-window approval. |
| Drive mutation | Missing file identity, sharing boundary, data class, approval, or rollback. |
| External communication | Missing exact approved content, sender, recipients, or channel. |
| Campaign activation or spend | Missing account, budget, activation approval, spend boundary, or stop condition. |
| Live automation | Missing owner, cadence, end condition, monitoring, or kill switch. |
| C4-C7 data action | Missing explicit data authorization, minimization, purpose, and transfer boundary. |

## Immediate Stop

Stop immediately if the request asks NEOS/NEXUS to infer authority, bypass access controls, conceal execution, or treat urgency as approval.
