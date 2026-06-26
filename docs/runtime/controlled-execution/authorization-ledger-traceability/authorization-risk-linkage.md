# Authorization Risk Linkage

## Purpose

This document defines how authorization ledger entries link to reviewed risks.

Risk linkage records governance evidence. It does not execute runtime, activate production, create agents, or accept risk by implication.

## Required Risk Fields

| Field | Requirement |
|---|---|
| risk_id | Unique identifier for the risk record. |
| related_ledger_entry | Ledger entry linked to the risk. |
| risk_category | Category of risk. |
| risk_level | Risk level at review time. |
| risk_owner | Human owner of the risk. |
| mitigation | Mitigation reviewed for the risk. |
| residual_risk | Residual risk after mitigation. |
| review_status | Review status and reviewer. |
| decision_impact | Impact on Go, No-Go, Conditional Hold, expiration, or invalidation. |

## Risk Rules

- Unreviewed critical risk blocks execution.
- Risk linkage is evidence, not permission.
- Historical Go is not current Go.
- Execution remains blocked until a future separately authorized execution action exists.

## Status

Version: v0.1.0
Scope: Documentary governance only
Execution status: blocked
