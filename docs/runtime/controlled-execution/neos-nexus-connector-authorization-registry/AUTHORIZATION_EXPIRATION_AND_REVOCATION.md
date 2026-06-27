# Authorization Expiration and Revocation v0.1.0

## Purpose

This document defines when NEOS/NEXUS authorizations expire, when they must be revoked, and how revocation affects connectors, tools, modes, data classes, pull requests, Head SHAs, and critical actions.

Authorization must be treated as narrow, temporary, scoped, and evidence-bound.

## Expiration Rules

An authorization expires when any documented expiration condition occurs, including:

- The approved action is completed.
- The approved pull request is merged, closed, superseded, or abandoned.
- The approved branch changes outside the authorized scope.
- The approved Head SHA changes.
- The approved block ends or is superseded.
- The approved connector, tool, mode, data class, repository, path, account, document, campaign, calendar, mailbox, or object changes.
- The time window expires.
- Required evidence is missing.
- A validation fails.
- Risk increases beyond the approved scope.
- Tiziano manually revokes authorization.

## Merge Authorization

Merge authorization is single-use and expires immediately after the authorized merge is executed.

No merge authorization carries forward to:

- Another PR.
- Another Head SHA.
- Another branch.
- Another block.
- Another connector.
- Another repository.
- Auto-merge.
- Production deployment.

Merge remains prohibited unless future explicit human authorization names the PR number and exact Head SHA.

## Manual Revocation

Tiziano may manually revoke any authorization at any time.

Manual revocation applies immediately to:

- Connector access.
- Tool use.
- Operational mode.
- Data class handling.
- PR operations.
- External communications.
- Automations.
- Production actions.
- Campaigns.
- Permission changes.
- Secrets or credentials workflows.

After revocation, NEOS/NEXUS must stop execution, preserve available evidence, avoid further mutation, and report the blocked or revoked state.

## Automatic Revocation

Authorization must be automatically revoked when any of the following occurs:

- Change of scope.
- Change of PR.
- Change of Head SHA.
- Change of branch target.
- Change of connector.
- Change of tool.
- Change of operational mode.
- Change of data class.
- Change of affected object.
- Incident.
- Error.
- Ambiguity.
- Security risk.
- Privacy risk.
- Legal, commercial, financial, or reputational risk.
- Unexpected sensitive data appears.
- Evidence is incomplete.
- Validation output contradicts expected state.

## No Inheritance

There is no inherited authorization between:

- PRs.
- Blocks.
- Connectors.
- Tools.
- Branches.
- Head SHAs.
- Repositories.
- Data classes.
- Operational modes.
- Accounts.
- Drive objects.
- Campaigns.
- Calendar events.
- Mail threads.
- Automations.
- Production surfaces.

Each authorization must stand on its own documentary record.

## Revocation Effects

When an authorization is revoked or expired, the affected action must be classified as:

| Condition | Required State |
| --- | --- |
| Authorization expired | Block or escalate. |
| Authorization revoked | Block. |
| Authorization ambiguous | Escalate or block. |
| Head SHA changed | Re-authorize before merge or critical execution. |
| PR changed | Re-authorize before merge or critical execution. |
| Connector changed | Re-authorize connector scope. |
| Data class elevated to C4-C7 | Stop and escalate. |
| MODE_5 requested | Block unless future specific authorization exists. |

## Evidence of Revocation

Revocation records should document:

- Revocation timestamp.
- Revoking party or automatic trigger.
- Affected authorization.
- Affected connector, tool, mode, data class, PR, Head SHA, object, or account.
- Reason.
- Last known safe state.
- Actions stopped.
- Evidence preserved.
- Required next step.

Without a valid active authorization, NEOS/NEXUS must not execute the action.
