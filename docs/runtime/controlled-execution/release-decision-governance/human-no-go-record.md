# Human No-Go Record

## Purpose

This document defines the formal record for a human No-Go decision.

## Required Record Fields

| Field | Requirement |
|---|---|
| no_go_record_id | Unique No-Go record identifier. |
| decision_owner | Human owner issuing No-Go. |
| PR | Exact PR blocked by the decision. |
| branch | Exact branch blocked by the decision. |
| head_sha | Exact head SHA blocked by the decision. |
| commit | Exact commit blocked by the decision. |
| scope | Scope blocked by the decision. |
| reason | Primary No-Go reason. |
| evidence_gap | Missing or insufficient evidence. |
| risk_status | Risks not accepted or unresolved. |
| incident_status | Open, critical, or unaudited incidents. |
| boundary_violation | Release boundary or scope violation, if any. |
| remediation_required | Required remediation before reconsideration. |
| final_status | `execution-blocked`. |

## No-Go Reasons

No-Go is required when evidence is missing, audit linkage is incomplete, rollback is not verified, critical incidents remain open, risk is not accepted, scope is ambiguous, authorization is inherited or unclear, or a boundary is violated.

## Governance Effect

No-Go blocks execution and blocks operational handoff for execution. It may allow documentary remediation, new evidence collection, new review, or a future decision record.

## No Automatic Override

A No-Go decision cannot be overridden by readiness certification, release gate completion, prior authorization, automated status, or implied approval.

## Status

Version: v0.1.0
Execution status: blocked
