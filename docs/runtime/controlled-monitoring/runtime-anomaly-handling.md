# Runtime Anomaly Handling

## Purpose

Define how future runtime anomalies must be handled during controlled
monitoring.

## Anomaly examples

- Unexpected state transition.
- Missing event.
- Unexpected event.
- Evidence capture failure.
- Audit linkage failure.
- Health degradation.
- Safety signal breach.
- Unauthorized scope expansion.
- Rollback readiness failure.
- Human escalation path unavailable.

## Handling rules

- Record anomaly evidence.
- Link anomaly to audit.
- Classify severity.
- Decide hold, stop, emergency pause, rollback or escalation.
- Preserve the exact monitoring boundary and runtime window.

## Escalation rule

High and critical anomalies require human escalation before continuation.
