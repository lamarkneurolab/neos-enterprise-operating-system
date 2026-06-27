# Evidence Correlation Index

## Purpose

This document defines the master correlation index for documentary evidence and audit traceability.

## Required Fields

| Field | Description |
|---|---|
| evidence_id | Stable identifier for the evidence record |
| evidence_type | PR, commit, check, audit event, decision, authorization, rollback, incident, handoff, expiration, invalidation, or blocked execution |
| source | Canonical or supporting evidence source |
| canonical_reference | GitHub URL, file path, PR number, commit SHA, check name, or ledger reference |
| related_block | Related Block 13, 14, 15, 16, 17, 18, or 19 |
| related_pr | Related PR number when applicable |
| branch | Related branch when applicable |
| base_sha | Base SHA for the relevant PR or comparison |
| head_sha | Head SHA for the relevant PR or comparison |
| merge_commit_sha | Merge commit SHA when a merge exists |
| check_status | Related check status summary |
| decision_id | Related Go / No-Go or release decision identifier |
| authorization_id | Related human authorization identifier |
| audit_event_id | Related audit event identifier |
| rollback_id | Related rollback identifier |
| incident_id | Related incident identifier |
| handoff_id | Related handoff identifier |
| expiration_id | Related expiration identifier |
| invalidation_id | Related invalidation identifier |
| blocked_execution_id | Related blocked execution identifier |
| review_status | Pending, reviewed, rejected, expired, invalidated, or superseded |
| human_reviewer | Named reviewer responsible for evidence review |
| notes | Additional documentary context |

## Correlation Rules

The index links evidence records. It does not convert evidence into authorization, release permission, production activation, runtime execution, or autonomous action.

## Review Expectations

Each correlation entry must be reviewed for source authority, completeness, staleness, conflict with newer records, and relationship to Block 18 authorization ledger records.

## Core Boundary

Evidence correlaciona. Auditoria verifica. Nada ejecuta.

## Status

Version: v0.1.0
Execution status: blocked
