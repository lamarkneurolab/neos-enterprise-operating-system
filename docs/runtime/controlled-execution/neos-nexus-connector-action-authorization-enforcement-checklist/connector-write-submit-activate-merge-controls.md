# Connector Write Submit Activate Merge Controls

## Purpose

These controls separate low-risk preparation from connector actions that require exact approval and evidence.

## Control Matrix

| Action class | Minimum enforcement |
| --- | --- |
| Write | Exact object, target, data class, account, approval, and rollback path. |
| Submit | Final payload, recipient or destination, sender identity if applicable, and approval of exact content. |
| Activate | Environment, trigger, budget or impact cap, owner, stop condition, monitoring, and explicit activation approval. |
| Merge | PR number, exact Head SHA, base branch, diff scope, review state, validation evidence, and explicit merge approval. |

## Always Block Without Approval

- Permission changes.
- External communications.
- Google Drive mutation.
- Campaign activation, serving, spend, billing, or budget change.
- Live automation.
- Secrets handling.
- Production mutation.
- C4-C7 data use.
- Merge or auto-merge.

## Enforcement Note

Creating or updating a pull request is not merge authorization. Merge authority must be separate and exact.
