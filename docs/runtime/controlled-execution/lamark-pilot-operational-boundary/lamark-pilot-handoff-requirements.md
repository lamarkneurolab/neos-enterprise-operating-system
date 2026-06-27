# Lamark Pilot Handoff Requirements

## Purpose

This document defines handoff requirements for the Lamark controlled pilot.

## Required Handoff Fields

| Field | Requirement |
|---|---|
| handoff_id | Stable handoff identifier |
| source_owner | Owner transferring responsibility |
| target_owner | Owner accepting responsibility |
| handoff_scope | Specific Lamark pilot scope |
| evidence_package | Evidence included in the handoff |
| audit_package | Audit events included in the handoff |
| authorization_status | Current authorization state |
| blocked_items | Blocked actions or unresolved incidents |
| open_items | Pending reviews or missing evidence |
| acceptance_status | Accepted, rejected, conditional, or pending |

## Required Handoff Scenarios

- Transition from boundary planning to sandbox review.
- Transition from sandbox review to evidence review.
- Transition from evidence review to audit review.
- Transition after incident detection.
- Transition after rollback review.
- Transition before any future request for operational expansion.

## Handoff Rules

Handoff transfers context and accountability. It does not transfer execution permission, production authorization, permission modification rights, document handling authority, or authorization for future PRs.

## Status

Version: v0.1.0
Execution status: blocked
