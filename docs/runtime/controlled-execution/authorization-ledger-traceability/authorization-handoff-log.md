# Authorization Handoff Log

## Purpose

This document defines how documentary handoffs are recorded for authorization and release decision traceability.

The handoff log transfers context only. It does not execute runtime, activate production, create agents, or transfer execution authority.

## Required Handoff Fields

| Field | Requirement |
|---|---|
| handoff_id | Unique identifier for the handoff record. |
| source_owner | Owner transferring context. |
| target_owner | Owner receiving context. |
| transferred_context | Context included in the handoff. |
| non_transferred_authority | Authority explicitly not transferred. |
| related_decision | Decision linked to the handoff. |
| related_authorization | Authorization linked to the handoff. |
| related_evidence | Evidence linked to the handoff. |
| execution_status_after_handoff | Execution status after the handoff. |

## Handoff Rules

- Handoff transfers context, not execution authority.
- Handoff does not authorize execution.
- Handoff does not supersede No-Go unless a valid new decision explicitly does so.
- Execution remains blocked until a future separately authorized execution action exists.

## Status

Version: v0.1.0
Scope: Documentary governance only
Execution status: blocked
