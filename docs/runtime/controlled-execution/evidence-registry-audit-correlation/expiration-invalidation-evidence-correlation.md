# Expiration and Invalidation Evidence Correlation

## Purpose

This document defines how expirations and invalidations are recorded and correlated with affected evidence, authorizations, and decisions.

## Required Fields

| Field | Description |
|---|---|
| expiration_id | Stable expiration identifier |
| invalidation_id | Stable invalidation identifier |
| affected_authorization | Authorization affected by expiration or invalidation |
| affected_decision | Decision affected by expiration or invalidation |
| affected_evidence | Evidence affected by expiration or invalidation |
| reason | Reason for expiration or invalidation |
| timestamp | Time the expiration or invalidation became effective |
| replacement_required | Whether replacement evidence, decision, or authorization is required |
| execution_impact | Blocked, no effect, review required, or superseded |

## Expiration and Invalidation Rules

- Expired or invalidated evidence cannot be used as active authorization.
- Expired authorization is historical evidence only.
- Invalidated decision evidence must not be treated as current Go.
- Replacement evidence does not authorize execution unless a separate future authorization exists.

## Review Requirements

Review must confirm affected records, reason, timestamp, replacement requirement, audit event, and whether execution remains blocked.

## Status

Version: v0.1.0
Execution status: blocked
