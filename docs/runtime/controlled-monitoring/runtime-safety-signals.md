# Runtime Safety Signals

## Purpose

Define safety signals for future controlled execution monitoring.

## Minimum safety signals

- Authorization remains valid.
- Scope remains locked.
- Runtime window remains valid.
- Monitoring boundary remains valid.
- Evidence capture is active.
- Audit linkage is active.
- Rollback readiness remains valid.
- Incident escalation path remains available.
- No unauthorized permission change.
- No unauthorized secret handling.
- No unauthorized dependency, service, runner, CI, database or integration.
- No agent creation.

## Safety levels

- normal
- watch
- degraded
- stop_required
- pause_required
- rollback_required
- human_escalation_required

## Safety rule

Safety signals must be evidenced and audited. Missing safety signal evidence
blocks continuation.
