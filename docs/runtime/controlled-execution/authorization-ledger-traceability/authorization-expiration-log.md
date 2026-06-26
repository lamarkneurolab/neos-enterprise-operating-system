# Authorization Expiration Log

## Purpose

This document defines how expirations of authorizations and decisions are recorded.

The expiration log records loss of validity. It does not execute runtime, activate production, create agents, or renew authorization.

## Required Expiration Fields

| Field | Requirement |
|---|---|
| expiration_id | Unique identifier for the expiration record. |
| related_authorization | Authorization affected by expiration. |
| related_decision | Decision affected by expiration. |
| expiration_trigger | Trigger that caused expiration. |
| expiration_date | Date and timestamp of expiration. |
| expired_scope | Scope no longer valid. |
| impact | Impact of expiration. |
| required_next_action | Required new review or authorization action. |
| execution_status_after_expiration | Execution status after expiration. |

## Expiration Rules

- Expired authorization cannot be reused.
- Historical Go is not current Go.
- Prior authorization is evidence, not permission.
- Execution remains blocked until a future separately authorized execution action exists.

## Status

Version: v0.1.0
Scope: Documentary governance only
Execution status: blocked
