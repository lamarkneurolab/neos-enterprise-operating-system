# Human Go Authorization

## Purpose

This document defines when a human Go decision is valid for release decision governance.

## Valid Go Conditions

A Go decision is valid only when a human authorizer explicitly approves the exact decision record with:

- PR number.
- Branch.
- Base SHA.
- Head SHA.
- Commit.
- Scope.
- Runtime window.
- Release boundary.
- Evidence package reference.
- Requested action.
- Expiration or scope limit.
- Decision timestamp.

## Non-Reusable Authorization

Human Go authorization is exact, limited, and non-reusable. It cannot transfer to another PR, branch, head SHA, commit, scope, runtime window, release boundary, or future action.

## Prohibited Interpretations

- Go does not execute.
- Go does not activate production.
- Go does not create agents.
- Go does not authorize integrations.
- Go does not modify permissions.
- Go does not authorize secrets, dependencies, CI, runners, databases, or services.
- Go does not permit future actions by inference.

## Required Human Authority

Tiziano or another explicitly named human decision owner must provide the Go decision. Automated systems may collect evidence or format records, but cannot grant Go authorization.

## Execution Boundary

Even after a valid Go decision, execution remains blocked until a future separately authorized execution action exists for the exact PR, branch, head SHA, commit, scope, action, runtime window, and monitoring boundary.

## Status

Version: v0.1.0
Execution status: blocked
