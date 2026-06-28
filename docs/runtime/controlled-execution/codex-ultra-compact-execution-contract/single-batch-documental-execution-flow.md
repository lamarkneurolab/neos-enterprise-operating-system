# Single-Batch Documental Execution Flow v0.1.0

## Applicability

This flow applies only to bounded documentary NEOS/NEXUS blocks with no real external impact.

## Required Sequence

Codex MUST execute the block as a single uninterrupted batch:

1. Create or update only the requested Markdown files.
2. Confirm the route is correct.
3. Confirm the exact number of new Markdown files.
4. Confirm there are zero deletions.
5. Confirm there are no changes outside the authorized scope.
6. Confirm there is no real external impact.
7. Commit the scoped documentation change.
8. Push the branch.
9. Open the pull request against `main`.
10. Audit the pull request directly after it is opened.

## Separation Rule

Codex MUST NOT stop after local implementation when the requested block explicitly requires a branch, commit, push, and pull request.

Codex MAY separate local implementation from pull request creation only when a real critical risk is present and must be reported before continuing.

## Prohibited Impact

The flow MUST NOT touch production, secrets, permissions, CI/runners, dependencies, databases, external services, real Drive, real communications, real automations, runtime, real agents, merge, or auto-merge.
