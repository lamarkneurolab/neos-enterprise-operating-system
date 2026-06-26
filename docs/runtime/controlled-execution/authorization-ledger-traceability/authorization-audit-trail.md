# Authorization Audit Trail

## Purpose

This document defines how authorization ledger entries connect to audit trail events.

The audit trail records changes and review events. It does not execute runtime, activate production, create agents, or grant permissions.

## Required Audit Fields

| Field | Requirement |
|---|---|
| audit_event_id | Unique identifier for the audit event. |
| ledger_entry_id | Ledger entry affected by the audit event. |
| actor | Human or system actor recording the documentary event. |
| action | Action performed on the ledger record. |
| timestamp | Date and time of the audit event. |
| before_state | State before the change. |
| after_state | State after the change. |
| reason | Reason for the change. |
| evidence_link | Evidence supporting the audit event. |
| review_status | Review status of the audit event. |

## Audit Rules

- Ledger changes must be auditable.
- Ledger changes must not erase historical state.
- Audit records are evidence, not permission.
- Ledger records do not execute.

## Status

Version: v0.1.0
Scope: Documentary governance only
Execution status: blocked
