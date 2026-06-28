# Multi-PR Execution Rules

## One block, one branch

Every block in a batch uses a separate branch created from main unless a different base is explicitly authorized. A branch must contain only the files required for that block.

## One block, one commit

Each block is committed once. Amendments are allowed only before PR creation and only when they preserve the single-commit requirement. Follow-up changes after review require a clear decision to amend or create a new commit.

## One block, one PR

Each block receives its own PR against main. PR text may reference the batch, but it must not imply shared approval, shared merge, or dependency-free approval for other PRs.

## PR content requirements

Each PR identifies title, objective, path, file list, validation performed, deletion count, and remaining merge authorization requirements.

## Cross-PR independence

No PR may require another PR to be merged unless the dependency is explicitly documented. If a dependency exists, the dependent PR must name the upstream PR and describe the effect of reviewing it independently.

## Merge restriction

Merge authority is never granted by batch execution. Each merge requires a human authorization naming the individual PR number and exact Head SHA for that PR.
