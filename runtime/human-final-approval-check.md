# Human Final Approval Check

## Purpose

Define the final human approval check before any future controlled execution
could be considered.

## Required authority

Tiziano is the human approving authority when explicit user authorization is
required for controlled activation or execution.

## Approval must specify

- authorizer
- activation_session_id
- PR
- branch
- head SHA
- commit
- scope
- action
- runtime window
- expiration or scope limit
- evidence reference
- audit reference

## Non-reuse rule

Approval applies only to the exact named session, PR, branch, head SHA, commit,
scope, action and runtime window. It is not reusable for future PRs, altered
branches, changed commits, expanded scopes or later runtime windows.
