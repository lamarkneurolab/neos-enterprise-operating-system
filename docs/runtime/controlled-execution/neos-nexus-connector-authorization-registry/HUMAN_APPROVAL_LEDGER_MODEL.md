# Human Approval Ledger Model v0.1.0

## Purpose

The Human Approval Ledger is the documentary model for recording human authorizations that control NEOS/NEXUS connector execution. It captures who authorized what, for which connector, tool, data class, operating mode, scope, time window, evidence record, and revocation rule.

The ledger documents authorization. It does not replace explicit authorization when a rule, risk class, pull request, Head SHA, data class, connector, or live action requires a new approval.

## Core Rule

Tiziano authorizes critical impact.

Critical impact includes, at minimum, production execution, merge, permission mutation, external communication, campaign activation, spend, billing, secrets, data classes C4-C7, live agents, live automations, final commercial proposals, invoices, or any action that can materially affect Lamark, NEOS, NEXUS, customers, accounts, assets, or third parties.

## Minimum Ledger Fields

| Field | Required | Description |
| --- | --- | --- |
| Date | Yes | Calendar date and timestamp of authorization or record creation. |
| Block | Yes | Governance block number and title. |
| Action | Yes | Specific action being authorized, prepared, escalated, blocked, or revoked. |
| Connector | Yes | Connector or integration involved. |
| Tool | Yes | Specific tool, command, API, UI, or runtime capability involved. |
| Data class | Yes | C0-C7 classification for the data touched by the action. |
| Operational mode | Yes | MODE_0 through MODE_5. |
| Authorizing party | Yes | Tiziano for critical actions, or approved non-critical authority where applicable. |
| Scope | Yes | Repository, path, PR, Head SHA, account, document, object, time window, or other bounded target. |
| Expiration | Yes | Date, event, PR closure, Head SHA change, merge completion, manual revocation, or other expiry condition. |
| Evidence | Yes | Links, hashes, command outputs, PR identifiers, screenshots, logs, or documentary references sufficient to audit the action. |
| Revocation | Yes | Manual or automatic revocation condition and revocation timestamp when applicable. |

## Recommended Extended Fields

| Field | Description |
| --- | --- |
| Authorization type | Prepare-only, execute-once, execute-until-expiry, read-only, write-documentation, critical-action, live-action, or revoked. |
| Risk class | Low, controlled, elevated, critical, or prohibited. |
| Validation performed | Pre-execution checks completed before action. |
| Result | Completed, blocked, escalated, failed, revoked, superseded, or expired. |
| Reversibility | Whether the action can be undone and the documented rollback path. |
| Related PR | Pull request number, base branch, branch name, and Head SHA. |
| Related commit | Commit SHA and commit message when relevant. |
| Related object | File, document, campaign, account, calendar event, message, automation, or runtime identifier. |

## Ledger Entry Template

| Field | Value |
| --- | --- |
| Date |  |
| Block |  |
| Action |  |
| Connector |  |
| Tool |  |
| Data class |  |
| Operational mode |  |
| Authorizing party |  |
| Scope |  |
| Expiration |  |
| Evidence |  |
| Revocation |  |
| Result |  |
| Reversibility |  |

## Authorization Boundaries

- A ledger entry must be narrow enough to evaluate independently.
- A ledger entry must not authorize unrelated connectors, tools, modes, data classes, repositories, branches, pull requests, accounts, or production objects.
- A merge authorization expires after the approved merge is executed.
- A PR authorization does not carry into a later PR.
- A Head SHA change invalidates approval unless the authorization explicitly permits that updated SHA.
- A connector authorization does not authorize another connector.
- A prepare-only authorization does not authorize execution.
- A documentation authorization does not authorize production use.

## Ledger Is Not a Runtime Permission Grant

The ledger does not create accounts, grant OAuth scopes, expose credentials, alter permissions, activate connectors, start automations, send communications, merge PRs, or move data. It records governance facts that NEOS/NEXUS must evaluate before attempting a controlled action.

If evidence is missing or the ledger conflicts with current scope, the action must be blocked or escalated.
