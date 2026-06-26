# Human Authorization Ledger

## Purpose

This document defines how explicit human authorizations are recorded for Runtime Controlled Execution Authorization Ledger & Release Decision Traceability v0.1.0.

The ledger captures authorization evidence. It does not execute runtime, activate production, create agents, or grant future permission by implication.

## Required Authorization Fields

| Field | Requirement |
|---|---|
| authorization_id | Unique identifier for the authorization record. |
| authorizing_human | Human who explicitly authorized the bounded action. |
| date | Date and timestamp of the authorization. |
| requested_action | Action requested before authorization. |
| authorized_action | Exact action authorized. |
| explicitly_excluded_action | Actions explicitly excluded from authorization. |
| repository | Canonical repository covered by the authorization. |
| pr_number | Exact PR covered, if applicable. |
| branch | Exact branch covered by the authorization. |
| base_sha | Exact base SHA reviewed. |
| head_sha | Exact head SHA reviewed. |
| commit_sha | Exact commit covered by the authorization. |
| merge_commit_sha | Merge commit, if the authorization covers a completed merge. |
| authorization_status | `active-for-record`, `expired`, `invalidated`, `superseded`, or `blocked`. |
| authorization_expiration | Expiration condition or timestamp. |
| authorization_invalidation_status | Invalidation state and reason. |
| evidence_references | Links to supporting evidence. |
| notes | Additional documentary context. |

## Authorization Rules

- Historical authorization is evidence, not active permission.
- Prior authorization is evidence, not permission.
- Anything not explicitly authorized remains blocked.
- Execution remains blocked until a future separately authorized execution action exists.
- Authorization for one PR does not authorize another PR.
- Authorization for one head SHA does not authorize a changed head SHA.

## Completion Requirements

Every human authorization entry must include enough evidence to determine who authorized what, when, for which repository, PR, branch, base SHA, head SHA, commit, merge commit, scope, and exclusions.

## Status

Version: v0.1.0
Scope: Documentary governance only
Execution status: blocked
