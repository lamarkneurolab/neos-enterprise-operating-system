# Commit SHA Evidence Registry

## Purpose

This document defines traceability for commits and SHAs used as evidence in controlled execution review.

## Required Fields

| Field | Description |
|---|---|
| commit_sha | Full Git commit SHA |
| commit_type | Feature, documentation, fix, merge, revert, or correction |
| source_branch | Branch containing the commit before merge |
| target_branch | Branch targeted by merge or review |
| related_pr | Related PR number |
| parent_sha | Parent commit SHA or SHAs |
| merge_commit_sha | Merge commit SHA when applicable |
| author | Commit author |
| timestamp | Commit timestamp |
| scope_summary | Documentary summary of the change |
| validation_status | Check, review, or manual validation status |
| authorization_status | Authorized for document change, expired, invalidated, absent, or not applicable |

## Commit Evidence Rules

- A commit proves change history; it does not grant operational permission.
- A head SHA proves the reviewed state for a PR; it does not authorize execution.
- A merge commit proves integration history; it does not activate production.
- Historical commit evidence is not current authorization.

## Review Requirements

Commit evidence must be correlated with the related PR, branch, base SHA, check status, human authorization reference if present, and audit event when available.

## Status

Version: v0.1.0
Execution status: blocked
