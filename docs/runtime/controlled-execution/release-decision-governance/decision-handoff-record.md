# Decision Handoff Record

## Purpose

This document defines the handoff record after a Go / No-Go release decision.

## Handoff Contents

The handoff must state:

- Decision record identifier.
- Decision type.
- Decision owner.
- Recipient.
- PR.
- Branch.
- Base SHA.
- Head SHA.
- Commit.
- Scope.
- Runtime window.
- Release boundary.
- Evidence package.
- Audit linkage.
- Risk review.
- Rollback confirmation.
- Incident review.
- Expiration rules.
- Invalidation rules.
- Execution restrictions.

## Handoff Rules

- Handoff transfers documentation, not execution authority.
- Handoff cannot expand scope.
- Handoff cannot activate production.
- Handoff cannot create agents or integrations.
- Handoff cannot modify permissions, secrets, dependencies, CI, runners, databases, services, or production configuration.
- Handoff remains blocked for execution unless a future separate execution authorization exists.

## No-Go Handoff

A No-Go handoff must clearly mark execution as blocked and list required remediation before any future decision review.

## Status

Version: v0.1.0
Execution status: blocked
