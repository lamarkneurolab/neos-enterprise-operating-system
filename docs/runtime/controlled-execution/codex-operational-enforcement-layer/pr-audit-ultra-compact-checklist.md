# PR Audit Ultra Compact Checklist v0.1.0

## Required Checks

- [ ] PR is opened against `main`.
- [ ] Branch contains one bounded enforcement change set.
- [ ] Changed files are Markdown-only or explicitly allowed lightweight configuration.
- [ ] PR description includes scope, evidence, risk, rollback path, PR URL, and Head SHA.
- [ ] No production, secrets, permissions, CI/runners, dependencies, databases, real Drive, real communications, real automations, runtime execution, real agents, deletions, merge, or auto-merge are included.
- [ ] The Codex Output Contract verifier has been completed.
- [ ] Human PR/merge authorization boundary has been reviewed.

## Pass Condition

The PR passes this audit only when every required check is true for the current Head SHA.

## Fail Condition

Any missing check, changed Head SHA after review, or blocked action requires correction before closure. Merge remains blocked until exact human authorization names the PR and current Head SHA.
