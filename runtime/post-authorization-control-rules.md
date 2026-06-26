# Post-Authorization Control Rules

## Purpose

Define controls that apply after a future execution authorization.

## After authorization

After authorization, the approved scope, PR, branch, head SHA, commit and
action must remain unchanged.

## Still prohibited

Even with authorization, NEOS must not perform unapproved:

- Scope expansion.
- Permission changes.
- Secret management.
- Dependency installation.
- External activation.
- Agent creation.
- Runner, CI, database or service creation.
- Destructive changes.

## Invalidation changes

New approval is required when scope, PR, branch, head SHA, commit, action,
risk, evidence, audit, rollback or incident plan changes.

## Evidence and audit continuity

Evidence and audit must be maintained from activation request through
post-authorization review and any future execution window.
