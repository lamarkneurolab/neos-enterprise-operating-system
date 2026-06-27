# Critical Action Evidence Requirements v0.1.0

## Purpose

Critical actions require enough evidence for NEOS/NEXUS and Tiziano to understand what was intended, what was authorized, what object was affected, what validation occurred, what result occurred, and whether the action can be reversed.

Without sufficient evidence, the action must be blocked or escalated.

## Critical Action Categories

The following actions are critical by default:

- Merge.
- Permission creation, modification, removal, or delegation.
- Google Drive sharing, moving, deletion, ownership change, or document mutation.
- External communications, including email, customer messages, public posts, partner messages, and final outbound documents.
- Campaign creation, activation, serving, spend, billing, or budget changes.
- Live automation.
- Live agents.
- Secrets or credentials handling.
- Production runtime changes.
- Production deployment.
- Data classes C4-C7.
- Facturas and invoices.
- Final proposals.
- Legal, commercial, financial, or identity-affecting commitments.

## Minimum Evidence Fields

Each critical action must record:

| Field | Description |
| --- | --- |
| Intention | Why the action is being considered and what outcome is expected. |
| Scope | Exact repository, PR, Head SHA, branch, connector, account, object, file, document, campaign, event, thread, or runtime surface. |
| Authorizing party | Tiziano for critical impact unless a future governance rule explicitly defines another authority. |
| Timestamp | Date and time of authorization, validation, execution, and result. |
| Affected object | The specific object that will be read, changed, merged, sent, shared, activated, billed, scheduled, or executed. |
| Pre-validation | Checks performed before execution, including status, diff, permissions, target, data class, risk, and reversibility. |
| Result | Completed, blocked, escalated, failed, revoked, expired, or partially completed. |
| Reversibility | Whether rollback is possible, how it would be performed, and what cannot be reversed. |

## Category-Specific Evidence

| Critical action | Additional evidence required |
| --- | --- |
| Merge | PR number, exact Head SHA, base branch, review state, diff scope, validation outputs, explicit merge authorization, and confirmation that authorization expires after merge. |
| Permissions | Current permission state, requested new state, affected principals, affected assets, reason, authorization, reversibility, and audit output. |
| Google Drive | File or folder identifier, current sharing state, requested action, affected users, data class, authorization, and rollback plan. |
| External communications | Recipients, final content, channel, sending identity, purpose, authorization, timestamp, and confirmation that the exact final message was approved. |
| Campaigns | Account, campaign, budget, bid, billing event, activation state, serving risk, creative, target, authorization, and spend boundary. |
| Live automations | Trigger, frequency, action boundary, spend or impact cap, data classes, stop condition, monitoring plan, authorization, and kill switch. |
| Secrets | Secure flow used, secret name or reference without value exposure, destination, access boundary, rotation expectation, and confirmation no secret value is logged or documented. |
| Production | Environment, service, deployment target, rollback path, health check, change window, authorizing party, and post-action verification. |
| C4-C7 data | Data class, source, purpose, minimization method, retention expectation, transfer boundary, authorization, and evidence that real sensitive data is not reproduced unnecessarily. |
| Facturas and invoices | Recipient, amount, currency, taxable entity, final document, authorization, and delivery method. |
| Final proposals | Recipient, final text, commercial terms, expiration, legal/commercial risk, authorization, and delivery method. |
| Live agents | Agent identity, tools, connectors, permissions, data classes, runtime boundary, stop condition, monitoring, authorization, and rollback or disable procedure. |

## Pre-Execution Checklist

Before any critical action, NEOS/NEXUS must verify:

- The action is explicitly authorized.
- The authorizing party is valid for the action type.
- The scope matches the requested action exactly.
- The operational mode permits execution.
- The connector and tool are authorized.
- The data class is allowed.
- Required evidence exists.
- The affected object is identified.
- Reversibility or irreversibility is documented.
- No expiration or revocation trigger has occurred.

## Block 29 Constraints

For this block, the following critical actions are not authorized for execution:

- Merge.
- Permission mutation.
- Google Drive mutation.
- External communication sending.
- Campaign activation or spend.
- Live automation activation.
- Secrets exposure.
- Production changes.
- Real C4-C7 data use.
- Invoices, final proposals, or live agents.

Documentation may describe these evidence requirements, but must not execute the underlying critical actions.

## Insufficient Evidence Rule

If evidence is absent, incomplete, stale, contradicted, or not tied to the exact action scope, NEOS/NEXUS must block or escalate the action.

Preparation may continue only when it does not expose sensitive data, change external systems, trigger live execution, or imply approval.
