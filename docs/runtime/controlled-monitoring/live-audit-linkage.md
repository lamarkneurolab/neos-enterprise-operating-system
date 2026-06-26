# Live Audit Linkage

## Purpose

Define how future live monitoring evidence must link to audit records.

## Minimum audit linkage

- activation_session_id
- go_no_go_decision
- monitoring_boundary
- runtime_window
- scope
- observed_signal
- evidence_reference
- drift_reference
- anomaly_reference
- stop_or_pause_reference
- rollback_reference
- human_escalation_reference

## Linkage rules

- Every live evidence record must have an audit path.
- Every drift, anomaly, stop, pause and rollback trigger must link evidence and
  audit.
- Audit linkage must preserve why a safeguard decision was made.
- Missing audit linkage blocks continuation.

## Non-audit-service rule

This document does not create audit services or external integrations. It
defines documentary audit linkage only.
