# Tool Mode Authorization Matrix v0.1.0

## Purpose

This matrix defines how NEOS/NEXUS should treat connector and tool actions across operational modes MODE_0 through MODE_5. It separates execution, preparation, escalation, and blocking decisions by tool category.

## Operational Modes

| Mode | Name | Meaning |
| --- | --- | --- |
| MODE_0 | Documentation Only | Create or update non-live governance documentation inside an approved scope. |
| MODE_1 | Read and Inspect | Read local or connected information within an approved scope without mutation. |
| MODE_2 | Prepare Draft | Prepare changes, drafts, plans, or proposed actions without external effect. |
| MODE_3 | Controlled Local Execution | Execute bounded local or repository actions that do not affect production or external parties. |
| MODE_4 | Critical Human-Approved Execution | Execute a critical action only after explicit human approval for exact scope, PR, Head SHA, object, and evidence. |
| MODE_5 | Live Automation Production | Autonomous or live production execution affecting external systems, spend, permissions, sensitive data, or third parties. |

MODE_5_LIVE_AUTOMATION_PRODUCTION is blocked by default and is not authorized by this block. It requires future specific authorization.

## Decision Terms

| Term | Meaning |
| --- | --- |
| Execute | The action may be performed within the exact approved scope and evidence requirements. |
| Prepare | The action may be drafted, modeled, or staged for review but not executed. |
| Escalate | Human approval is required before proceeding. |
| Block | The action must not proceed under the current authorization. |

## Matrix

| Tool or connector category | MODE_0 | MODE_1 | MODE_2 | MODE_3 | MODE_4 | MODE_5 |
| --- | --- | --- | --- | --- | --- | --- |
| Reading local repository documentation | Execute | Execute | Execute | Prepare | Escalate if critical | Block |
| Writing Markdown documentation in approved path | Execute | Prepare | Execute | Execute if path-limited | Escalate if critical | Block |
| Git status, diff, branch inspection | Execute | Execute | Execute | Execute | Escalate if critical | Block |
| Git branch creation for approved block | Prepare | Execute | Execute | Execute | Escalate if scope changes | Block |
| Git commit for approved documentation scope | Prepare | Prepare | Prepare | Execute | Escalate if scope changes | Block |
| Git push for approved branch | Prepare | Prepare | Prepare | Execute | Escalate if scope changes | Block |
| GitHub PR creation against main | Prepare | Prepare | Prepare | Execute when approved by task scope | Escalate if target, branch, or scope changes | Block |
| GitHub merge | Block | Block | Prepare only | Escalate | Execute only with explicit PR number and exact Head SHA approval | Block |
| GitHub auto-merge activation | Block | Block | Block | Block | Escalate only under future explicit authorization | Block |
| Technical execution outside approved repo scope | Block | Block | Escalate | Escalate | Escalate | Block |
| Google Drive read | Prepare | Escalate unless explicitly scoped | Escalate | Block | Escalate | Block |
| Google Drive create, move, delete, share, permission change | Block | Block | Prepare only if explicitly requested | Block | Execute only with explicit object-level approval | Block |
| Google Docs, Sheets, Slides mutation | Block | Escalate | Prepare only | Block | Execute only with explicit document-level approval | Block |
| Gmail or external email read | Block | Escalate | Escalate | Block | Execute only with explicit mailbox/thread approval | Block |
| Gmail or external email send | Block | Block | Prepare draft only if explicitly requested | Block | Execute only with explicit recipient/content approval | Block |
| Calendar read | Block | Escalate | Prepare | Block | Execute only with explicit calendar scope approval | Block |
| Calendar create, update, delete, invite response | Block | Block | Prepare only if explicitly requested | Block | Execute only with explicit event-level approval | Block |
| Campaign or ads read | Block | Escalate | Prepare | Block | Execute only with explicit account scope approval | Block |
| Campaign creation, activation, spend, billing, serving | Block | Block | Prepare only if explicitly requested | Block | Escalate for future authorization | Block |
| Automation documentation | Execute | Execute | Execute | Prepare | Escalate if critical | Block |
| Automation creation or scheduling | Block | Block | Prepare only | Escalate | Execute only with explicit bounded approval | Block |
| Live automation, live agents, recurring autonomous execution | Block | Block | Block | Block | Escalate for future authorization | Block |
| Secrets, credentials, API keys | Block | Escalate metadata only | Block | Block | Execute only through approved secure flow, never exposed in docs | Block |
| Production deployment or production runtime change | Block | Block | Prepare | Block | Execute only with explicit production approval | Block |
| Final proposals, invoices, legal/commercial commitments | Block | Block | Prepare | Block | Execute only with explicit final approval | Block |

## Mandatory Blocks in Block 29

The following are blocked in this block:

- Production live execution.
- MODE_5_LIVE_AUTOMATION_PRODUCTION.
- Sending external communications.
- Activating campaigns.
- Activating live automations.
- Modifying permissions.
- Moving, deleting, sharing, or modifying Google Drive objects.
- Using real secrets.
- Using real sensitive data in classes C4-C7.
- Merging any PR without explicit authorization naming the PR number and exact Head SHA.

## Escalation Rule

If a tool category, operational mode, connector, data class, object, or affected party is not clearly covered by an active authorization, NEOS/NEXUS must escalate to Tiziano or block the action.
