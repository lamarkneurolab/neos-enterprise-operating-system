# Authorization Invalidation Log

## Purpose

This document defines how invalidations of authorizations and decisions are recorded.

The invalidation log records loss of support for execution. It does not execute runtime, activate production, create agents, or replace required human authorization.

## Required Invalidation Fields

| Field | Requirement |
|---|---|
| invalidation_id | Unique identifier for the invalidation record. |
| related_authorization | Authorization affected by invalidation. |
| related_decision | Decision affected by invalidation. |
| invalidation_reason | Reason for invalidation. |
| invalidation_trigger | Event or condition that triggered invalidation. |
| invalidation_date | Date and timestamp of invalidation. |
| invalidated_scope | Scope invalidated. |
| required_review | Required review before any future action. |
| execution_status_after_invalidation | Execution status after invalidation. |

## Invalidation Rules

- Invalidated authorization cannot support execution.
- Invalidated authorization cannot be reused.
- No-Go remains blocking until superseded by a valid new decision.
- Execution remains blocked until a future separately authorized execution action exists.

## Status

Version: v0.1.0
Scope: Documentary governance only
Execution status: blocked
