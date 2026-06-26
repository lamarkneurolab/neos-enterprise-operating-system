# Authorization Incident Linkage

## Purpose

This document defines how authorization ledger entries link to incident status, incident review, remediation, and execution impact.

Incident linkage records governance evidence. It does not execute runtime, activate production, create agents, or close incidents by implication.

## Required Incident Fields

| Field | Requirement |
|---|---|
| incident_id | Unique identifier for the incident record. |
| related_ledger_entry | Ledger entry linked to the incident. |
| incident_status | Current incident state. |
| incident_review_status | Review status and reviewer. |
| incident_impact | Impact on authorization or release decision. |
| required_remediation | Remediation required before future action. |
| decision_impact | Impact on Go, No-Go, Conditional Hold, expiration, or invalidation. |
| execution_status | Execution status after incident review. |

## Incident Rules

- Unresolved blocking incident prevents execution.
- Incident linkage is evidence, not permission.
- No-Go blocks execution.
- Execution remains blocked until a future separately authorized execution action exists.

## Status

Version: v0.1.0
Scope: Documentary governance only
Execution status: blocked
