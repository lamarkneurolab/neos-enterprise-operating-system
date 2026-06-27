# Lamark Pilot Audit Requirements

## Purpose

This document defines audit requirements for the Lamark controlled pilot.

## Events Requiring Audit

- Human authorization grant, denial, expiration, or invalidation.
- Sandbox boundary definition or change.
- Data access request and approval.
- Real document access request and approval.
- Document classification activity.
- Sensitive information detection.
- Blocked action detection.
- Evidence package review.
- Rollback trigger or rollback review.
- Incident detection, escalation, or closure.
- Handoff request, transfer, acceptance, or rejection.

## Audit Fields

| Field | Requirement |
|---|---|
| audit_event_id | Stable audit identifier |
| actor | Human or system actor creating the event record |
| timestamp | Event time |
| event_type | Authorization, evidence, data, document, sensitive information, rollback, incident, handoff, or blocked action |
| related_evidence | Evidence record link |
| related_authorization | Authorization record link when applicable |
| review_status | Pending, reviewed, blocked, accepted, rejected, expired, or invalidated |

## Audit Rule

Audit verifies traceability. Audit does not grant permission, authorize execution, activate production, or override blocked actions.

## Status

Version: v0.1.0
Execution status: blocked
