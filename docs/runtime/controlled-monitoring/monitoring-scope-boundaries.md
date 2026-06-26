# Monitoring Scope Boundaries

## Purpose

Define the allowed boundary for future controlled execution monitoring.

## Boundary fields

- PR.
- Branch.
- Head SHA.
- Commit.
- Scope.
- Action.
- Runtime window.
- Runtime area.
- Health signals.
- Safety signals.
- Evidence capture points.
- Audit linkage points.
- Rollback trigger points.
- Human escalation path.

## Boundary rules

- Monitoring must not observe or affect unapproved runtime areas.
- Monitoring must not expand scope.
- Monitoring must not introduce new services or integrations.
- Boundary changes require renewed authorization.

## Blocking rule

If the monitoring boundary is missing, stale or exceeded, controlled execution
must be held or stopped.
