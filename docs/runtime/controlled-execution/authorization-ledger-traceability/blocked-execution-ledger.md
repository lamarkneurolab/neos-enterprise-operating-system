# Blocked Execution Ledger

## Purpose

This document defines the ledger for requested, implied, expired, invalidated, out-of-scope, or explicitly denied actions that remain blocked.

The blocked execution ledger records blocked status. It does not execute runtime, activate production, create agents, or unblock action by implication.

## Required Blocked Action Fields

| Field | Requirement |
|---|---|
| blocked_action_id | Unique identifier for the blocked action. |
| requested_action | Action requested or implied. |
| blocking_reason | Reason the action is blocked. |
| related_decision | Decision linked to the block. |
| related_authorization | Authorization linked to the block. |
| related_risk | Risk linked to the block. |
| related_incident | Incident linked to the block. |
| required_unblock_condition | Exact condition required before the action can be reconsidered. |
| current_execution_status | Current execution status after the block is recorded. |

## Blocking Rules

- Blocked means blocked.
- Absence of permission means blocked.
- Historical Go does not unblock execution.
- No-Go remains blocking until superseded by a valid new decision.
- Execution remains blocked until a future separately authorized execution action exists.

## Status

Version: v0.1.0
Scope: Documentary governance only
Execution status: blocked
