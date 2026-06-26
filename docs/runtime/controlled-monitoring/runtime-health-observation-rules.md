# Runtime Health Observation Rules

## Purpose

Define the health signals that must be observable for future controlled
execution monitoring.

## Minimum health signals

- Execution state.
- Task queue state.
- Event bus state.
- State manager transition status.
- Runtime availability.
- Latency or response posture.
- Error posture.
- Evidence capture status.
- Audit capture status.
- Rollback readiness status.
- Incident posture.

## Observation rules

- Health observation must stay inside the approved monitoring boundary.
- Health signals must be linked to evidence and audit records.
- Missing health signals block continuation.
- Degraded health requires hold, stop, pause or escalation review.

## Non-service rule

This document does not create telemetry, monitoring services, dashboards,
runners or integrations. It defines required documentary signals only.
