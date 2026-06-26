# Go/No-Go Decision Protocol

## Purpose

Define the final human decision required before any future controlled execution
could be considered.

## Allowed decisions

- go
- no-go
- hold
- abort
- needs-review

## Go requirements

A `go` decision requires:

- Valid Block 12 authorization reference.
- Activation session record.
- Locked scope.
- Defined execution window.
- Sufficient pre-activation evidence.
- Pre-activation audit record.
- Rollback readiness.
- Post-activation monitoring preconditions.
- Explicit human approval for the exact PR, branch, head SHA, commit, scope,
  action and runtime window.

## No automatic approval

Go/no-go cannot be inferred from dry-run pass, activation request approval,
execution authorization, execution window definition or handoff.
