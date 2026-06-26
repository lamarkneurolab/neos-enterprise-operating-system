# Live Evidence Capture Rules

## Purpose

Define how evidence must be captured during a future controlled execution.

## Evidence moments

- Before start.
- At start.
- During monitored checkpoints.
- At drift or anomaly detection.
- At stop, pause or rollback trigger.
- At completion or handoff.

## Minimum fields

- evidence_id
- timestamp
- activation_session_id
- monitoring_boundary
- runtime_window
- observed_signal
- expected_value
- observed_value
- decision_reference
- audit_reference
- rollback_reference
- reviewer

## Sufficiency rules

Evidence is sufficient only when it is current, scoped, traceable, linked to
audit and able to support rollback or escalation review.

## Non-execution rule

Evidence capture rules do not execute runtime or activate services.
