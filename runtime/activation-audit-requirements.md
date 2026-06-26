# Activation Audit Requirements

## Purpose

Define audit requirements for activation decisions.

## Minimum audit fields

| Field | Requirement |
|---|---|
| `audit_id` | Stable audit identifier. |
| `activation_request_id` | Linked activation request. |
| `decision` | Approval, denial, deferral, block or abort. |
| `authorizer` | Human authorizer when applicable. |
| `scope` | Exact scope. |
| `pr` | Linked PR. |
| `branch` | Linked branch. |
| `head_sha` | Linked head SHA. |
| `commit` | Linked commit. |
| `evidence_reference` | Evidence package reference. |
| `risk_reference` | Risk acceptance reference. |

## Authorization record

Authorization must link the approval decision and exact scope.

## Rejection record

Denial, deferral, block and abort decisions must record reason and next action.

## Post-authorization record

Any change after authorization must be recorded and evaluated for invalidation.

## Core log relationship

Activation audit must link `logs/AUDIT_TRAIL.md` and `logs/DECISION_LOG.md`.

## Block 13 audit handoff

Block 13 requires `runtime/audit-record-before-activation.md` before final
go/no-go. A Block 12 audit record does not replace the pre-activation audit.
