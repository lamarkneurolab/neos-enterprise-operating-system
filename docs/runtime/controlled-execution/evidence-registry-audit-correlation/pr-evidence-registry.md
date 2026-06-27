# PR Evidence Registry

## Purpose

This document defines how PR evidence is registered for controlled execution audit correlation.

## Required Fields

| Field | Description |
|---|---|
| pr_number | GitHub PR number |
| pr_title | GitHub PR title |
| pr_state | Open, closed, merged, draft, or superseded |
| pr_url | Canonical GitHub PR URL |
| base_branch | Target branch |
| head_branch | Source branch |
| base_sha | Base SHA at review time |
| head_sha | Head SHA at review time |
| merge_commit_sha | Merge commit SHA when merged |
| changed_files | Files changed by the PR |
| additions | Added lines reported by GitHub |
| deletions | Deleted lines reported by GitHub |
| checks | Check names and conclusions |
| review_status | Pending, reviewed, approved, changes requested, or not applicable |
| merge_authorization_reference | Link to relevant human authorization or decision record when present |
| execution_status | Blocked unless a separate future execution action exists |

## PR Evidence Rules

- A merged PR is historical evidence, not runtime authorization.
- An open PR is proposed change evidence, not execution permission.
- A passing PR check is validation evidence, not release authorization.
- A merge authorization reference does not authorize future runtime execution.

## Lamark Pilot Boundary

PR evidence related to Lamark must be treated as controlled pilot documentation only. It must not be used to start open production, external customer workflows, sales actions, financial processing, or autonomous document operations.

## Status

Version: v0.1.0
Execution status: blocked
