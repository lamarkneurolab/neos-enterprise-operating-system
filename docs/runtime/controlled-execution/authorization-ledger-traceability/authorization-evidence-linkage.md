# Authorization Evidence Linkage

## Purpose

This document defines how authorization ledger entries link to supporting evidence.

Evidence linkage records documentary support. It does not execute runtime, activate production, create agents, or authorize future action.

## Required Evidence Fields

| Field | Requirement |
|---|---|
| evidence_id | Unique identifier for the evidence record. |
| evidence_source | Canonical source of the evidence. |
| evidence_type | Type of evidence, such as PR, commit, check, review, approval, log, or document. |
| related_block | Related NEOS block, including Blocks 13, 14, 15, 16, or 17. |
| related_pr | PR associated with the evidence. |
| related_commit | Commit associated with the evidence. |
| related_decision | Decision linked to the evidence. |
| related_authorization | Authorization linked to the evidence. |
| evidence_completeness_status | Completeness status of the evidence. |
| evidence_review_status | Review status and reviewer. |
| evidence_retention_expectation | Retention requirement for audit use. |

## Evidence Rules

- No ledger entry should be treated as complete without evidence linkage.
- Evidence supports traceability; evidence does not execute.
- Prior authorization is evidence, not permission.
- Historical Go is not current Go.

## Status

Version: v0.1.0
Scope: Documentary governance only
Execution status: blocked
