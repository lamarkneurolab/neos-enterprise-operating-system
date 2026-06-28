# Authorization Trigger Map

## Purpose

This map identifies when NEOS/NEXUS must obtain exact human authorization before continuing.

## Authorization Triggers

| Trigger | Authorization must name |
| --- | --- |
| GitHub merge | PR number, exact Head SHA, base branch, and merge method. |
| GitHub branch or PR write | Repository, branch, PR or path, action, and scope. |
| Permission change | Affected principal, asset, current state, target state, and reversibility. |
| Google Drive mutation | File or folder, account, operation, sharing boundary, data class, and rollback. |
| External communication | Channel, sender, recipient list, exact content, timing, and approval source. |
| Campaign action | Account, campaign, budget or spend boundary, activation state, creative, and stop condition. |
| Live automation | Trigger, cadence, owner, target systems, end condition, kill switch, and monitoring. |
| Secrets handling | Secure flow, destination, secret reference without value exposure, and access boundary. |
| Production change | Environment, service, deployment target, change window, health check, and rollback. |
| C4-C7 data | Data class, source, purpose, minimization, transfer boundary, and retention expectation. |

## Non-Transfer Rule

Approval for preparation does not authorize live execution. Approval for one object, account, PR, branch, payload, or Head SHA does not transfer to another.
