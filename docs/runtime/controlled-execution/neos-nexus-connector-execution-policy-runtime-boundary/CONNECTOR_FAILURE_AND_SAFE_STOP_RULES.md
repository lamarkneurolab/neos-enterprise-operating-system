# Connector Failure and Safe Stop Rules

## Safe-stop triggers

A connector action stops immediately when authorization cannot be verified, the target differs from the recorded scope, a tool requests broader permissions, a credential or secret appears, restricted data is detected, the environment is production without approval, or the connector response is ambiguous.

## Failure classes

| Failure class | Response |
| --- | --- |
| Authorization mismatch | Stop, record mismatch, and escalate with the requested and authorized scopes. |
| Data boundary breach | Stop, avoid further inspection, and record only minimum metadata needed for audit. |
| External effect uncertainty | Stop before submit, send, publish, merge, activate, or schedule. |
| Tool capability drift | Stop when the tool can perform more than the authorized action requires. |
| Partial execution | Stop subsequent steps, record completed effects, and prepare recovery handoff. |
| Audit evidence gap | Stop execution and downgrade to prepare or escalate. |

## Recovery posture

Recovery is documentation-first unless a separate rollback authorization exists. The operator prepares a factual handoff containing the connector, action, scope, last known safe state, observed failure, completed side effects, and recommended next human decision.

## Retry rules

Retries are allowed only for prepare-only local actions that do not expand scope. Retrying connector execution requires confirming that the authorization remains valid and that the failure was transient, bounded, and not caused by scope mismatch or policy violation.

## Incident linkage

Any blocked or failed connector action that could affect production, external recipients, sensitive data, billing, campaign state, or automation state must link to the incident or risk log before further work continues.
