# Rollback Evidence Correlation

## Purpose

This document defines the evidence required to correlate rollback readiness, rollback decisions, and rollback outcomes.

## Required Fields

| Field | Description |
|---|---|
| rollback_trigger | Condition or event that requires rollback review |
| rollback_scope | Explicit scope of rollback consideration |
| rollback_reference | Canonical or supporting rollback record |
| related_decision | Go / No-Go or rollback decision reference |
| related_authorization | Human authorization reference when present |
| related_incident | Incident reference when present |
| related_audit_event | Audit event linked to rollback evidence |
| evidence_required_before_rollback | Evidence package required before rollback |
| evidence_required_after_rollback | Evidence package required after rollback |

## Rollback Rules

Rollback evidence supports review. It does not execute rollback, modify production, change permissions, move documents, delete files, or transform real data.

## Review Requirements

Rollback evidence must confirm trigger, scope, decision state, authorization state, incident linkage, audit linkage, expected outcome, and post-rollback closure evidence.

## Status

Version: v0.1.0
Execution status: blocked
