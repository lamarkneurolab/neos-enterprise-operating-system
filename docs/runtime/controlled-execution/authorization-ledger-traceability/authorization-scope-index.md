# Authorization Scope Index

## Purpose

This document defines how authorized scope, explicitly excluded scope, blocked scope, and out-of-bound actions are mapped for the authorization ledger.

The scope index is documentary only. It does not execute runtime, activate production, create agents, or grant operational permission.

## Required Scope Fields

| Field | Requirement |
|---|---|
| scope_id | Unique identifier for the scope record. |
| authorized_scope | Exact scope explicitly authorized. |
| explicitly_excluded_scope | Exact scope explicitly excluded. |
| blocked_scope | Scope that remains blocked. |
| out_of_bound_actions | Actions outside authorization boundaries. |
| scope_expiration | Expiration condition or timestamp. |
| scope_invalidation | Invalidation trigger and status. |
| scope_owner | Human owner of the scope definition. |
| scope_evidence | Evidence supporting the scope record. |
| scope_audit_linkage | Audit references for scope creation or change. |

## Scope Rules

- Anything not explicitly authorized remains blocked.
- Prior authorization is evidence, not permission.
- Authorization for one PR, branch, base SHA, head SHA, commit, or merge commit does not extend to another unless explicitly recorded.
- Execution remains blocked until a future separately authorized execution action exists.

## Status

Version: v0.1.0
Scope: Documentary governance only
Execution status: blocked
