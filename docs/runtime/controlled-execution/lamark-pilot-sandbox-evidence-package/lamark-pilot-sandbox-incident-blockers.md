# Lamark Pilot Sandbox Incident Blockers

## Purpose

This document defines incident blockers for Lamark sandbox preparation.

## Blocking Incidents

The following incidents block sandbox readiness:

- Unauthorized access to real documents.
- Unauthorized movement, deletion, sharing, sending, permission change, or transformation of real documents.
- Introduction of sensitive financial data.
- Introduction of real customer data.
- Exposure of credentials, secrets, tokens, or private keys.
- Attempted production activation.
- Attempted runtime execution.
- Attempted autonomous action.
- Attempted external commercial diagnosis.
- Attempted external sales activity.
- Missing or invalid human authorization.
- Missing evidence record.
- Missing audit correlation.
- Unresolved rollback trigger.

## Blocker Rule

When an incident blocker is present, the sandbox remains blocked until the incident is reviewed, evidenced, and closed by a human approver.

## Status

Version: v0.1.0
Execution status: blocked
