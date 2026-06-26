# Final Handoff Rules

## Purpose

Define how closure context may be handed off to a later block.

## Heritable context

- Closure decision.
- Final evidence package.
- Audit closure record.
- Rollback outcome.
- Incident linkage status.
- Unresolved risk register.
- Human closure approval.
- Lessons learned.

## Blocked context

Handoff does not carry authorization to execute runtime, activate production,
create agents, create integrations, modify permissions, manage secrets, install
dependencies, create CI, create runners, create databases or create services.

## New work requirement

Every later block requires new scope, new authorization, new branch, new commit,
new PR and explicit merge authorization.

## No automatic continuation

Final handoff does not trigger future implementation or merge.
