# Human Merge Authorization Boundary v0.1.0

## Merge Boundary

Codex MUST NOT merge and MUST NOT activate auto-merge.

Merge requires exact human authorization.

## Exact Authorization Requirements

Human merge authorization MUST name:

1. The exact pull request.
2. The exact Head SHA.

Authorization that omits either value is invalid.

## Exhaustion Rule

Human merge authorization is single-use and is exhausted immediately after it is executed.

No authorization carries forward to later pull requests, later Head SHAs, later blocks, or later process steps.

## Head SHA Expiration Rule

If the Head SHA changes after authorization is granted, the authorization expires immediately.

A new authorization must then name the exact pull request and the new exact Head SHA.

## Scope Exclusions

This boundary does not authorize production actions, secrets handling, permission changes, CI/runner changes, dependency changes, database changes, external service operations, real Drive operations, real communications, real automations, C4-C7 data handling, deletions, destructive changes, runtime execution, real agent activation, merge by Codex, or auto-merge.
