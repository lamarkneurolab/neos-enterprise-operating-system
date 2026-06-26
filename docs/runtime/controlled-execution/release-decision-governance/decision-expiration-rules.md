# Decision Expiration Rules

## Purpose

This document defines when a Go / No-Go decision expires.

## Expiration Triggers

A release decision expires when any of the following occurs:

- Head SHA changes.
- Commit changes.
- Branch changes.
- PR changes.
- Scope changes.
- Runtime window expires.
- Release boundary changes.
- Evidence becomes stale.
- Audit linkage breaks.
- New incident appears.
- New risk appears.
- Rollback becomes invalid.
- Human authorization expiration is reached.

## Expiration Effect

An expired decision cannot support execution, handoff, or future authorization. A new decision record and explicit human review are required.

## No Inference Rule

An expired Go cannot be revived by readiness certification, release gate status, prior merge authorization, or implied continuity.

## Required Expiration Record

The record must state the trigger, timestamp, affected decision, decision owner, evidence impact, risk impact, rollback impact, and required next action.

## Status

Version: v0.1.0
Execution status: blocked
