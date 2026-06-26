# Post-Monitoring Review

## Definition

Post-monitoring review is the documentary review that occurs after a future
controlled execution monitoring window closes.

## Required inputs

- Activation session reference.
- Human go/no-go reference.
- Authorized PR, branch, head SHA, base SHA and commit.
- Authorized scope and action.
- Runtime window.
- Monitoring boundary.
- Live evidence package.
- Audit linkage.
- Drift and anomaly records.
- Stop, pause, rollback and incident records when applicable.

## Signals reviewed

- Runtime health signals.
- Runtime safety signals.
- Evidence capture status.
- Audit linkage status.
- Drift status.
- Anomaly status.
- Stop and emergency pause status.
- Rollback trigger status.
- Human escalation status.

## Post-monitoring states

- execution_completed
- execution_paused
- execution_invalidated
- incident_open
- rollback_review_required
- closure_review_required

## Incomplete review conditions

Review is incomplete when evidence, audit, incident linkage, rollback outcome,
scope validation, boundary validation or human closure approval is missing.
