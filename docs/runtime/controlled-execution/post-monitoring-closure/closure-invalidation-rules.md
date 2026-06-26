# Closure Invalidation Rules

## Purpose

Define conditions that invalidate documentary closure.

## Invalidation conditions

- Missing human approval.
- Incomplete evidence.
- Scope exceeded.
- Closure boundary violated.
- Monitoring boundary violated.
- Critical incident open.
- Critical rollback pending.
- Audit trail inconsistent.
- SHA, PR or branch mismatch.
- Base SHA mismatch when required.
- Destructive changes detected.
- Permission changes without authorization.
- Secret handling without authorization.
- Dependency changes without authorization.
- Runner, CI, database, service, integration or agent creation without
  authorization.

## Invalidation outcome

Invalid closure must move to `closure_invalidated`, `incident_escalated` or
`rollback_required` according to the evidence and risk posture.

## Reconsideration rule

Invalidated closure requires renewed review, corrected evidence, audit linkage,
human approval and, when applicable, rollback or incident resolution.
