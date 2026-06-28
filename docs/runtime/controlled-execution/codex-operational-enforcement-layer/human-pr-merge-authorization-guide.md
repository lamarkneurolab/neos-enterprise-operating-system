# Human PR/Merge Authorization Guide v0.1.0

## Minimum Human Authorization

Merge authorization is valid only when a human explicitly names:

- PR number or canonical PR URL.
- Current Head SHA.

## Invalid Authorization

Authorization is invalid when it is implied, historical, copied from another PR, missing the Head SHA, missing the PR identity, or issued before the final reviewed Head SHA exists.

## SHA Change Rule

Any new commit changes the Head SHA and expires prior merge authorization. Review and authorization must be repeated for the new Head SHA.

## Codex Boundary

Codex may prepare, push, open, and audit the PR when authorized by the task. Codex must not merge, enable auto-merge, alter permissions, or treat PR creation as execution approval.
