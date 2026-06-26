# Decision Change Control

## Purpose

This document defines how changes after a Go / No-Go decision are handled.

## Material Changes

Material changes include any change to:

- PR.
- Branch.
- Base SHA.
- Head SHA.
- Commit.
- Scope.
- Requested action.
- Runtime window.
- Release boundary.
- Runtime target.
- Monitoring boundary.
- Evidence package.
- Audit linkage.
- Risk profile.
- Rollback readiness.
- Incident status.
- Human decision owner.

## Change Control Rules

- Every material change requires a new evaluation.
- Every material change requires new explicit human authorization if a Go decision is sought again.
- A prior Go cannot be reused after material change.
- A No-Go remains blocking until explicitly superseded by a new decision record.

## Change Record Fields

| Field | Requirement |
|---|---|
| change_id | Unique change identifier. |
| prior_decision_id | Decision affected by the change. |
| changed_field | Field that changed. |
| old_value | Prior value. |
| new_value | New value. |
| impact | Evidence, risk, rollback, incident, or scope impact. |
| required_action | New review, No-Go, Hold, or invalidation. |

## Status

Version: v0.1.0
Execution status: blocked
