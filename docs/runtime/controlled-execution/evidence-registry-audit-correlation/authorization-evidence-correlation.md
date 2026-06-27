# Authorization Evidence Correlation

## Purpose

This document defines how evidence is linked to human authorization records.

## Required Fields

| Field | Description |
|---|---|
| authorization_id | Stable authorization identifier |
| authorizing_person | Named human authorizer |
| scope | Explicit authorized documentary scope |
| timestamp | Authorization timestamp |
| target_pr | Target PR when applicable |
| target_sha | Target SHA when applicable |
| authorized_action | Explicitly authorized action |
| expiration_condition | Condition that ends authorization validity |
| invalidation_condition | Condition that invalidates authorization |
| related_evidence | Evidence records supporting review of the authorization |

## Authorization Rules

- Prior authorization is evidence, not permission for future actions.
- Authorization must be explicit, scoped, current, and linked to the action being evaluated.
- The authorization for PR #16 is historical evidence only and must not be used for Block 19 authorization.
- Evidence linked to an authorization does not expand the authorized action.

## Review Requirements

Authorization evidence must be checked for named human authorizer, scope, target PR, target SHA, authorized action, expiration, invalidation, audit event, and conflict with later records.

## Status

Version: v0.1.0
Execution status: blocked
