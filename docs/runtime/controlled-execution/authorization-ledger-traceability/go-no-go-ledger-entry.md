# Go No-Go Ledger Entry

## Purpose

This document defines the standard ledger entry for Go, No-Go, and Conditional Hold decisions.

The entry records decision history. It does not execute runtime, activate production, create agents, or authorize future execution by implication.

## Required Decision Fields

| Field | Requirement |
|---|---|
| decision_id | Unique identifier for the decision. |
| decision_type | `go`, `no-go`, or `conditional-hold`. |
| decision_owner | Human owner of the decision. |
| decision_date | Date and timestamp of the decision. |
| decision_scope | Exact scope covered by the decision. |
| decision_evidence | Evidence reviewed for the decision. |
| decision_risk_status | Reviewed risk state and residual risk. |
| decision_rollback_status | Rollback confirmation state. |
| decision_incident_status | Incident review and unresolved incident state. |
| decision_expiration | Expiration condition or timestamp. |
| decision_invalidation_conditions | Conditions that invalidate the decision. |
| decision_supersession_status | Whether a later decision supersedes this one. |
| execution_status_after_decision | Execution status after recording the decision. |

## Decision Rules

- Go does not execute.
- No-Go blocks execution.
- Conditional Hold blocks execution until resolved.
- Historical Go is not current Go.
- No-Go remains blocking until superseded by a valid new decision.
- Execution remains blocked until a future separately authorized execution action exists.

## Invalid Decision Conditions

A decision entry is invalid if the decision owner, date, type, scope, evidence, risk status, rollback status, incident status, expiration, invalidation conditions, or execution status after decision is missing or ambiguous.

## Status

Version: v0.1.0
Scope: Documentary governance only
Execution status: blocked
