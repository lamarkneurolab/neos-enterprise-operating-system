# Authorization Rollback Linkage

## Purpose

This document defines how authorization ledger entries link to rollback plans, rollback evidence, and rollback confirmation.

Rollback linkage records readiness evidence. It does not execute runtime, activate production, create agents, or trigger rollback.

## Required Rollback Fields

| Field | Requirement |
|---|---|
| rollback_id | Unique identifier for the rollback linkage record. |
| related_ledger_entry | Ledger entry linked to rollback. |
| rollback_plan_reference | Reference to rollback plan or rollback playbook. |
| rollback_confirmation_status | Confirmation state for rollback readiness. |
| rollback_owner | Human owner of rollback review. |
| rollback_evidence | Evidence supporting rollback readiness. |
| rollback_readiness | Readiness status after review. |
| decision_impact | Impact on Go, No-Go, Conditional Hold, expiration, or invalidation. |

## Rollback Rules

- Unconfirmed rollback blocks execution.
- Rollback linkage is evidence, not permission.
- Go does not execute.
- Execution remains blocked until a future separately authorized execution action exists.

## Status

Version: v0.1.0
Scope: Documentary governance only
Execution status: blocked
