# Evidence Requirement Map

## Purpose

This map defines the minimum evidence needed to make connector decisions reviewable without repeating full policy text.

## Minimum Evidence

| Evidence field | Required content |
| --- | --- |
| Intention | Why the action is requested and expected outcome. |
| Scope | Exact connector, account, environment, object, file, branch, PR, Head SHA, or payload. |
| Authorization | Human approver, timestamp, and exact approved action. |
| Data class | Allowed classification and handling boundary. |
| Pre-validation | Status, diff, target, permissions, risk, and reversibility checks. |
| Result | Completed, prepared, escalated, blocked, failed, revoked, expired, or partially completed. |
| Rollback | Recovery path or documented irreversibility. |

## Critical Evidence Additions

| Action | Additional evidence |
| --- | --- |
| Merge | PR number, exact Head SHA, base branch, diff scope, validation outputs, and merge authorization. |
| Communication | Exact final content, recipients, sender, channel, and send approval. |
| Automation | Trigger, cadence, owner, stop condition, monitoring, and kill switch. |
| Campaign | Account, budget, bid, billing event, activation state, target, and spend boundary. |
| Drive mutation | File or folder identity, sharing state, affected users, data class, and rollback plan. |

## Evidence Boundary

Evidence must not include secret values, unnecessary restricted data, or implied approval language.
