# Human Escalation Rules

## Purpose

Define when future controlled monitoring must escalate to a human reviewer.

## Escalation triggers

- High or critical health degradation.
- High or critical safety signal.
- Scope drift.
- Runtime window breach.
- Monitoring boundary breach.
- Missing evidence or audit.
- Rollback trigger.
- Emergency pause.
- Safeguard failure.
- Ambiguous continuation decision.

## Required authority

Tiziano remains the explicit human authorizer when future controlled execution,
merge, activation, runtime action or critical continuation requires user
authorization.

## Traceability

Escalation must record authorizer, scope, PR, branch, head SHA, commit, action,
runtime window, monitoring boundary, evidence and audit references.

## Non-reuse rule

Escalation decisions are not reusable across PRs, branches, commits, scopes,
windows or monitoring boundaries.
