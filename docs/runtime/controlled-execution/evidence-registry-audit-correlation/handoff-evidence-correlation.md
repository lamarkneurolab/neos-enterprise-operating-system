# Handoff Evidence Correlation

## Purpose

This document defines evidence required for handoff between owners, reviewers, blocks, or governance stages.

## Required Fields

| Field | Description |
|---|---|
| handoff_id | Stable handoff identifier |
| source_owner | Owner transferring responsibility |
| target_owner | Owner receiving responsibility |
| handoff_scope | Explicit scope of the handoff |
| evidence_package | Evidence included in the handoff |
| open_items | Items not resolved at handoff time |
| blocked_items | Items that block execution or review |
| review_status | Pending, accepted, rejected, expired, invalidated, or superseded |
| acceptance_status | Accepted, conditionally accepted, rejected, or not reviewed |

## Handoff Rules

- Handoff evidence transfers context, not execution authority.
- Acceptance of a handoff is not release authorization.
- Open and blocked items must remain visible until separately resolved.
- Historical handoff evidence is not current authorization.

## Review Requirements

Handoff evidence must be reviewed for completeness, owner clarity, unresolved risks, blocked execution status, linked decisions, linked authorizations, and audit events.

## Status

Version: v0.1.0
Execution status: blocked
