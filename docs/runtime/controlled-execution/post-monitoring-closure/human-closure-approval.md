# Human Closure Approval

## Purpose

Define the explicit human approval required for documentary closure.

## Minimum fields

- authorizer
- PR
- branch
- head SHA
- base SHA
- closure scope
- closure boundary
- final evidence package
- audit closure record
- rollback outcome
- incident linkage status
- unresolved risk status
- final decision
- expiration or scope limit

## Authorizing user

Tiziano is the required human authorizer when closure approval requires explicit
user authorization.

## No implicit authorization

Closure approval is not implied by passing checks, completed monitoring, closed
PR review, previous authorization, branch status or merge status.

## Non-reuse rule

Closure approval applies only to the exact PR, branch, head SHA, base SHA,
closure scope, closure boundary and final decision.
