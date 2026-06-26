# Execution Abort Conditions

## Purpose

Define conditions that abort a future activation session before execution.

## Abort conditions

- PR, branch, head SHA or commit changed after authorization.
- Scope or action expanded.
- Human approval is absent, revoked or mismatched.
- Evidence is insufficient after review.
- Audit record is missing or invalid.
- Rollback readiness failed.
- Incident risk is high or critical and unresolved.
- Emergency stop condition is identified.
- Permissions, secrets, dependencies, agents, integrations, CI, runners,
  databases or services are introduced without authorization.
- Any destructive action appears in the activation path.

## Abort outcome

Abort closes the current activation path. A new request, review, authorization
and activation session are required before reconsideration.
