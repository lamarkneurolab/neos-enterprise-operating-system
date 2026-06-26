# Decision Audit Linkage

## Purpose

This document defines how a Go / No-Go decision must link to audit records, evidence records, approval history, invalidations, scope changes, and handoff records.

## Required Audit Links

- Release decision record.
- Evidence package.
- Final readiness certification.
- Release gate decision framework.
- Human Go authorization or Human No-Go record.
- Risk review.
- Rollback confirmation.
- Incident review.
- Expiration rule acknowledgement.
- Invalidation rule acknowledgement.
- Change control record.
- Handoff record.

## Audit Fields

| Field | Requirement |
|---|---|
| audit_entry_id | Unique audit reference. |
| actor | Human or system recording the entry. |
| decision_owner | Human decision owner. |
| timestamp | Audit timestamp. |
| PR | Exact PR. |
| branch | Exact branch. |
| head_sha | Exact head SHA. |
| commit | Exact commit. |
| decision | Go, No-Go, Conditional Hold, or Invalidated Decision. |
| evidence_links | Linked evidence package records. |
| change_links | Linked scope or decision changes. |

## Traceability Rules

The decision must be traceable from intake through evidence review, audit review, risk review, rollback review, incident review, decision, and handoff. Any broken trace blocks Go.

## Status

Version: v0.1.0
Scope: Documentary governance only
