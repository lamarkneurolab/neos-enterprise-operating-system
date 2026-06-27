# Lamark Pilot Final Rollback Scorecard

## Purpose

This scorecard defines final rollback readiness criteria for the Lamark pilot readiness decision gate.

## Scorecard

| Criterion | Required Condition | Gate Impact |
|---|---|---|
| Rollback scope | Rollback scope is documented for any future execution request | Required |
| Rollback owner | Human rollback owner is named | Required |
| Trigger list | Proposed rollback triggers are documented | Required |
| Stop condition | Stop condition is explicit and reviewable | Required |
| Production rollback | No production rollback is required by this documentary gate | Blocking |
| Reversibility gaps | Gaps are listed and dispositioned | Required |

## Passing Rule

Rollback readiness passes only when future rollback ownership, triggers, and stop conditions are documented without requiring live production changes.

## Failure Rule

Any missing rollback owner, missing trigger, non-reversible condition, required production rollback, or unresolved rollback gap fails this scorecard.

## Status

Version: v0.1.0
Scorecard status: documentary readiness only
Execution status: blocked
