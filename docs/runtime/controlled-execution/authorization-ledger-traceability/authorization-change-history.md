# Authorization Change History

## Purpose

This document defines how historical changes to authorization ledger records are documented.

Change history preserves traceability. It does not execute runtime, activate production, create agents, or modify runtime authorization state.

## Required Change Fields

| Field | Requirement |
|---|---|
| change_id | Unique identifier for the change record. |
| ledger_entry_affected | Ledger entry affected by the change. |
| change_type | Type of change, such as correction, supersession, expiration, invalidation, or review update. |
| change_reason | Reason for the change. |
| previous_state | State before the change. |
| new_state | State after the change. |
| approver | Human approver for the documentary change. |
| evidence | Evidence supporting the change. |
| audit_reference | Audit event linked to the change. |

## Change Rules

- Ledger changes must not erase historical state.
- Corrections must be traceable.
- Supersession must identify the superseding record.
- Prior authorization is evidence, not permission.
- Ledger records do not execute.

## Status

Version: v0.1.0
Scope: Documentary governance only
Execution status: blocked
