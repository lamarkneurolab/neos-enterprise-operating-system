# Blocked Execution Evidence Registry

## Purpose

This document defines evidence records for actions that remain blocked under controlled execution governance.

## Required Fields

| Field | Description |
|---|---|
| blocked_execution_id | Stable blocked execution identifier |
| blocked_action | Action that is not permitted |
| block_reason | Reason the action is blocked |
| related_no_go | Related No-Go decision when present |
| related_missing_authorization | Missing authorization record when applicable |
| related_missing_evidence | Missing evidence record when applicable |
| related_risk | Related risk or incident when applicable |
| required_resolution | Required documentary resolution before reconsideration |
| status | Blocked, under review, superseded, expired, invalidated, or resolved |

## Blocking Rules

- No-Go blocks execution until superseded by a valid new decision.
- Missing authorization blocks execution.
- Missing evidence blocks review completeness but does not create permission.
- Blocked execution evidence records the block; it does not resolve the block.

## Restricted Actions

Blocked actions include runtime execution, production activation, business agent creation, external integration creation, runner creation, CI creation, database creation, service creation, permission modification, secret administration, dependency installation, destructive change, merge without authorization, autonomous action, and real document movement without explicit authorization.

## Status

Version: v0.1.0
Execution status: blocked
