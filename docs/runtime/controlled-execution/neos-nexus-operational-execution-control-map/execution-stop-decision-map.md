# Execution Stop Decision Map

## Purpose

This map converts missing authority, unclear scope, and unsafe connector conditions into fast stop decisions.

## Stop Decision Map

| Condition | Decision | Allowed next movement |
| --- | --- | --- |
| Scope is unclear | Escalate | Ask for exact connector, account, object, branch, PR, path, or payload. |
| Authorization is missing | Stop | Prepare a handoff naming the missing approval. |
| Authorization is stale, revoked, contradicted, or broader than the action | Stop | Request fresh exact authorization. |
| Head SHA mismatch on merge | Block | Require new PR number and exact current Head SHA approval. |
| Data class is unknown | Escalate | Classify before read, write, submit, activate, or merge. |
| Secrets could be exposed | Block | Use secure flow only; do not record secret values. |
| Live external effect is possible | Escalate | Require exact approval and evidence before execution. |
| Production, campaign, automation, permission, Drive, or communication boundary is incomplete | Block | Prepare non-live evidence packet only. |
| User requests ultra-compact output | Execute compactly | Do not omit required stop condition. |

## Stop Language

Use short, exact wording: blocked action, missing requirement, and safe next step. Do not add policy exposition unless requested.
