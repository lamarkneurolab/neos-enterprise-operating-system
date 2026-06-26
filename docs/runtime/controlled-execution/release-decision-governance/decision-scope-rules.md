# Decision Scope Rules

## Purpose

This document defines the exact scope boundaries required for any Go / No-Go decision.

## Authorizable Scope Fields

A release decision may cover only an exact:

- PR.
- Branch.
- Base SHA.
- Head SHA.
- Commit.
- Requested action.
- Runtime window.
- Release boundary.
- Runtime target.
- Monitoring boundary.
- Evidence package.
- Rollback reference.
- Incident review reference.

## Boundary Rules

- Scope must be specific enough to audit.
- Scope must exclude all unreviewed runtime areas.
- Scope must identify prohibited actions.
- Scope must not rely on prior PR authorizations.
- Scope must not include production activation unless a future separate authorization explicitly allows it.

## Invalidation by Difference

Any difference in PR, branch, head SHA, commit, requested action, runtime window, release boundary, runtime target, evidence package, rollback reference, or incident status invalidates the decision.

## Prohibited Scope Expansion

A release decision cannot expand itself to agents, integrations, secrets, permissions, dependencies, CI, runners, databases, services, production configuration, or real execution.

## Status

Version: v0.1.0
Scope: Documentary governance only
