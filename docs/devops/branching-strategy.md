# Branching Strategy

## Main branch

`main` is protected conceptually as the canonical stable branch.

## Working branches

Use:

- `codex/<short-description>` for Codex-generated changes.
- `docs/<short-description>` for documentation-only branches.
- `infra/<short-description>` for infrastructure changes.

## Pull requests

All non-trivial changes should enter through PRs with evidence and rollback notes.
