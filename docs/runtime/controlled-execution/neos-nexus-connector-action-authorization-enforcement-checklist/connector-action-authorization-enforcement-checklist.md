# Connector Action Authorization Enforcement Checklist

## Purpose

This checklist converts prior connector authorization, execution-boundary, batch-governance, and playbook policies into a compact pre-action enforcement gate.

## Enforcement Gate

| Check | Required verification |
| --- | --- |
| Human authorization | Exact approval exists for this action. |
| Scope | Repository, PR, Head SHA, branch, file, account, object, environment, or connector target is exact. |
| Connector | Requested connector and tool are authorized. |
| Action type | Read, draft, write, submit, activate, merge, delete, notify, or schedule is classified. |
| Data class | Data class is known and permitted. |
| Risk | Critical action status and reversibility are recorded. |
| Evidence | Authorization, validation, and result evidence can be preserved. |
| Stop condition | Missing, stale, contradicted, or broader approval blocks execution. |

## Default Decision

If any required verification fails, do not execute. Prepare only when preparation has no external effect, no restricted data exposure, and no implied approval.
