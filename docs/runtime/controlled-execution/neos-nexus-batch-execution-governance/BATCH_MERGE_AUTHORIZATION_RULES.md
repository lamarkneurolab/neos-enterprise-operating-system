# Batch Merge Authorization Rules

## No batch merge authority

Batch execution never authorizes merge. Review completion, documentation readiness, and PR creation are not merge approvals.

## Required merge approval

Each PR requires a separate human authorization that names the exact PR number and exact Head SHA. The authorization applies only to that PR and only while the Head SHA remains unchanged.

## Head SHA drift

If a PR receives any new commit, amended commit, rebase, merge update, or force push, the previous merge authorization expires. A new exact Head SHA approval is required.

## Auto-merge

Auto-merge is blocked unless separately authorized for the individual PR by exact PR number and exact Head SHA. Batch language cannot authorize auto-merge across multiple PRs.

## Merge sequencing

When PRs are independent, they may be authorized in any order. When dependency rules name a merge order, downstream PRs require revalidation after upstream merge and before their individual merge authorization.

## Authorization record

The merge authorization record captures PR number, repository, base branch, Head SHA, approver, timestamp, validation evidence, and whether auto-merge remains blocked or separately allowed.
