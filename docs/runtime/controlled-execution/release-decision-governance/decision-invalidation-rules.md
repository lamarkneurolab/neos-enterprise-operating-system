# Decision Invalidation Rules

## Purpose

This document defines conditions that invalidate a release decision.

## Invalidation Conditions

- Ambiguous authorization.
- Inherited authorization.
- Changed PR.
- Changed branch.
- Changed head SHA.
- Changed commit.
- Changed scope.
- Changed runtime window.
- Changed release boundary.
- Missing evidence.
- Stale evidence.
- Broken audit linkage.
- New incident.
- New unaccepted risk.
- Rollback no longer verifiable.
- Handoff attempts outside the decision boundary.
- Any attempt to treat Go as execution authorization.

## Invalidation Effect

Invalidation blocks execution and requires a new review cycle. The prior decision becomes historical only and cannot authorize future work.

## Required Invalidation Record

The invalidation record must include the invalidated decision, trigger, timestamp, actor, decision owner notification, evidence impact, risk impact, rollback impact, incident impact, and required next action.

## Status

Version: v0.1.0
Execution status: blocked
