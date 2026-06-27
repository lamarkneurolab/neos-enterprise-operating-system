# NEOS + NEXUS Connector Authorization Registry v0.1.0

## Purpose

This registry defines the documentary authorization state for connectors, tools, operational modes, data classes, and critical actions used by NEOS, NEXUS, and Lamark-controlled execution surfaces.

The registry is not a runtime secret store, permission system, connector configuration file, or production activation mechanism. It is a control document used to determine whether a connector action may be executed, prepared for review, escalated to Tiziano, or blocked.

## Authorization Principles

- No connector, tool, mode, data class, or action receives implicit authorization.
- Availability does not imply authorization.
- Prior block approval does not authorize future pull requests, future Head SHAs, future connectors, future data classes, or future production actions.
- Critical impact requires explicit human authorization from Tiziano.
- When authorization is ambiguous, expired, missing, or contradicted by risk, the action must be blocked or escalated.
- This block does not authorize live production execution, live automations, external communications, campaign activation, permission changes, Google Drive mutation, or use of real sensitive data in classes C4-C7.

## Connector State Definitions

| State | Meaning | Execution Implication |
| --- | --- | --- |
| Available | The connector or tool exists as a possible capability in the environment, product, platform, or roadmap. | No execution rights. It may be documented only. |
| Connected | The connector appears technically reachable, installed, configured, authenticated, or visible to an operator. | No execution rights unless separately authorized. |
| Authorized | Tiziano or an approved governance record has granted a bounded authorization for a connector, tool, data class, mode, scope, and time window. | The action may proceed only within the documented scope. |
| Executable | The connector action is both technically possible and authorized for the current block, object, Head SHA, data class, mode, and evidence requirements. | Execution may proceed only if all required validations pass. |
| Live | The connector can affect production, external parties, spend, permissions, sensitive data, legal/commercial commitments, or autonomous runtime behavior. | Blocked by default. Requires future explicit authorization naming the PR number and exact Head SHA. |

## Registry Fields

Each connector authorization entry should document at minimum:

| Field | Description |
| --- | --- |
| Connector | Human-readable connector name, such as GitHub, Google Drive, Gmail, Calendar, Ads Manager, automation runtime, local shell, or document system. |
| Tool | Specific tool, command family, API surface, or integration feature. |
| Current state | Available, connected, authorized, executable, live, blocked, or revoked. |
| Authorized modes | MODE_0 through MODE_5 values permitted for the connector. |
| Authorized data classes | C0 through C7 classes permitted for the connector. |
| Authorized actions | Specific reads, writes, preparations, commits, pushes, PR creation, or other bounded operations. |
| Blocked actions | Explicitly prohibited operations for the connector. |
| Scope | Repository, path, document, campaign, account, file, calendar, mailbox, thread, or other bounded target. |
| Expiration | Date, event, PR closure, Head SHA change, merge completion, or manual revocation condition. |
| Evidence | Required record before and after the action. |
| Authorizing party | Tiziano for critical impact, or the approved governance mechanism for non-critical bounded actions. |

## Connector Categories

| Category | Examples | Default Block 29 Position |
| --- | --- | --- |
| Read-only documentation | Local Markdown reads, repository inspection, controlled diff review | May be used within approved repository scope. |
| Documentation writing | Markdown creation under the authorized path | May be executed only inside the approved Block 29 path. |
| Technical execution | Git branch, status, diff, commit, push, PR creation | Permitted only for the approved branch and PR workflow; merge is prohibited without future explicit authorization. |
| External communication | Gmail, public posts, messages, customer communications | Blocked. May prepare drafts only if separately authorized. |
| Google Drive | Docs, Sheets, Slides, Drive files, sharing, movement, deletion | Mutation blocked. No moving, deleting, sharing, or permission changes. |
| Calendar | Event reads, event creation, attendee changes | Live scheduling and attendee changes blocked unless specifically authorized. |
| Campaigns and ads | Ads Manager, billing, spend, creative activation | Activation, spend, billing, and serving blocked. |
| Automations | Monitors, scheduled runs, live agents, recurring tasks | Live automation blocked. Documentation only in this block. |
| Secrets and credentials | API keys, tokens, passwords, private credentials | Real secrets and credential exposure blocked. |

## Relationship to NEOS, NEXUS, and Lamark

NEOS uses this registry as the governance reference for controlled execution. NEXUS uses it to determine whether an operational request is executable, preparable, escalatable, or blocked. Lamark uses it as part of the documentary control plane for enterprise AI operations, connector governance, and human approval traceability.

The registry is intentionally conservative. It does not activate connectors, grant platform permissions, create credentials, or authorize production behavior by itself.

## No Implicit Authorization

An action must not be inferred as authorized because:

- A connector is installed, visible, authenticated, or technically reachable.
- A previous block approved a related capability.
- A prior PR was merged.
- A branch was pushed.
- A draft or documentation record exists.
- A user generally requested progress on the platform.
- A tool can technically perform the operation.

When in doubt, NEOS/NEXUS must select the safer state: prepare, escalate, or block.
