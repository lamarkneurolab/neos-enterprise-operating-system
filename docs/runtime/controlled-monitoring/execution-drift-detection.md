# Execution Drift Detection

## Purpose

Define how future controlled execution drift must be detected and handled.

## Drift definition

Execution drift is any deviation between approved scope, action, runtime window,
monitoring boundary, expected signal or authorized state and the observed
runtime posture.

## Drift classes

- Scope drift.
- Timing drift.
- State transition drift.
- Evidence drift.
- Audit drift.
- Health signal drift.
- Safety signal drift.
- Rollback readiness drift.

## Drift handling

Drift must be classified as `low`, `medium`, `high`, `critical` or `blocked`.
High, critical and blocked drift require immediate human escalation and may
trigger hold, stop, emergency pause or rollback.

## Blocking rule

Unclassified or unaudited drift blocks continuation.
