# Execution Start Conditions

## Purpose

Define the documentary conditions that must exist before a future controlled
execution start can be considered.

## Required start conditions

- Activation session is valid.
- Scope lock is active.
- Execution window is defined.
- Preconditions verification passed.
- Pre-activation evidence is complete.
- Pre-activation audit is complete.
- Rollback readiness is documented.
- Monitoring preconditions are mapped.
- Human final approval is explicit.
- Go decision is recorded.

## Non-start rule

This document does not start execution. Start conditions describe future
eligibility only.

## Blocking rule

If any start condition is absent, stale or ambiguous, execution remains blocked.
