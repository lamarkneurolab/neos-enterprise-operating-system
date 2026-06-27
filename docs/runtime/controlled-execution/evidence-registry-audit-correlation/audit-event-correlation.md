# Audit Event Correlation

## Purpose

This document defines how evidence is correlated with audit events for controlled execution traceability.

## Required Fields

| Field | Description |
|---|---|
| audit_event_id | Stable audit event identifier |
| event_type | Review, authorization, decision, invalidation, expiration, rollback, incident, handoff, or blocked execution |
| event_timestamp | Timestamp of the audit event |
| actor | Human or system actor that produced the event record |
| related_evidence_id | Evidence record linked to the event |
| related_authorization_id | Authorization record linked to the event when present |
| related_decision_id | Decision record linked to the event when present |
| source_reference | Canonical GitHub source or supporting reference |
| audit_status | Pending, reviewed, accepted, rejected, expired, invalidated, or superseded |
| review_required | Whether human review is required |

## Audit Rules

- Audit correlation is traceability, not permission.
- Audit events verify evidence relationships; they do not grant authorization.
- Historical audit events cannot be reused as current Go decisions.
- Audit gaps must be recorded as incomplete evidence.

## Review Requirements

Audit correlation must check actor identity, event timestamp, source reference, related evidence, related decision, related authorization, and conflicts with later invalidation or expiration records.

## Status

Version: v0.1.0
Execution status: blocked
