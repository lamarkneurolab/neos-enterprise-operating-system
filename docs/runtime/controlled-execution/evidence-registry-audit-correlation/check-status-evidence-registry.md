# Check Status Evidence Registry

## Purpose

This document defines how check status evidence is registered and interpreted.

## Required Fields

| Field | Description |
|---|---|
| check_name | Name of the check |
| check_provider | GitHub Actions, GitHub status, manual validation, or other source |
| status | Queued, in progress, completed, missing, or skipped |
| conclusion | Success, failure, cancelled, neutral, timed out, action required, or not applicable |
| started_at | Check start timestamp |
| completed_at | Check completion timestamp |
| related_pr | Related PR number |
| related_commit | Related commit SHA |
| failure_summary | Failure context when applicable |
| required_for_review | Whether the check is required for document review |
| release_authorization_effect | Always none |

## Check Evidence Rules

- Passing checks are validation evidence, not release authorization.
- Failed checks are blocking review evidence until resolved or explicitly waived by a separate authorized documentary decision.
- Missing checks must be recorded as incomplete evidence.
- Checks do not execute runtime, activate production, or authorize future actions.

## Review Requirements

Check evidence must be reviewed against the PR head SHA, expected Markdown validation, and any repository-required checks that already exist. Block 19 does not create new CI.

## Status

Version: v0.1.0
Execution status: blocked
