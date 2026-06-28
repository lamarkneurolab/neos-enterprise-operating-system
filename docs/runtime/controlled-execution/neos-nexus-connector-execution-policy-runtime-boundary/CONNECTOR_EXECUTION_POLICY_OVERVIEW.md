# NEOS + NEXUS Connector Execution Policy Runtime Boundary v0.1.0

## Purpose

This policy converts the connector authorization ledger into a runtime boundary for deciding whether an action may be executed, prepared, escalated, or blocked. It applies to connector-mediated operations across NEOS and NEXUS when a tool, mode, data class, or risk condition could change production state, expose sensitive information, or trigger an external effect.

## Policy posture

Connector activity remains documentation-first unless a valid human authorization explicitly permits a bounded action. The default decision is prepare or block, not execute, whenever scope, data class, destination, identity, rollback posture, or audit evidence is incomplete.

## Decision classes

| Decision | Meaning | Minimum condition |
| --- | --- | --- |
| Execute | Perform the connector action in the authorized boundary. | Exact connector, tool, account, environment, data class, risk tier, time window, rollback path, and approver are recorded. |
| Prepare | Draft, validate, stage, simulate, or assemble evidence without external effect. | The action has no live production mutation, no real communication, no credential exposure, and no C4-C7 data handling. |
| Escalate | Pause for human review before action. | The request is ambiguous, higher risk than the current grant, or dependent on missing authorization evidence. |
| Block | Refuse operational movement. | The action touches prohibited data, production live effects, secrets, unapproved communications, unapproved automations, campaign activation, merge, or auto-merge. |

## Scope

This boundary covers GitHub, Google Drive, communication, automation, campaign, and orchestration connectors. It also covers local tool use when the tool is acting as a proxy for a connector action or producing handoff material that could later be executed.

## Non-goals

This policy does not grant operational authority, replace human approval, authorize production activation, authorize real customer communications, or permit handling of restricted C4-C7 data. It is a control surface for interpreting recorded authorization, not a substitute for it.

## Required audit evidence

Every connector decision records the requested action, requested connector, data class, environment, decision class, reason, authorization reference, evidence reference, operator, timestamp, and safe-stop condition. Missing evidence downgrades execute to escalate or block.
