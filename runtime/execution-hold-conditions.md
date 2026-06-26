# Execution Hold Conditions

## Purpose

Define conditions that place a future activation session on hold before
execution.

## Hold conditions

- Evidence is incomplete.
- Audit is incomplete.
- Runtime window is missing or expired.
- Scope lock needs review.
- Risk acceptance is stale.
- Rollback readiness is incomplete.
- Incident response mapping is incomplete.
- Final human approval is pending.
- Governance or certification review is unresolved.
- Markdown validation or repository validation is pending.

## Hold outcome

Hold pauses the activation path. It does not authorize execution and does not
invalidate the session unless the unresolved condition changes scope, risk,
authorization or runtime window.
