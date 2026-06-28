# Codex Ultra Compact Execution Contract v0.1.0

## Purpose

This contract defines the Ultra Compact operating rule for Codex when executing bounded NEOS/NEXUS documentary blocks with no real external impact.

## Execution Contract

For bounded documentary blocks, Codex MUST work in one single batch:

1. Implement the requested Markdown documentation.
2. Validate scope.
3. Commit.
4. Push.
5. Open a pull request against `main`.
6. Audit the pull request directly after opening it.

Codex MUST NOT split local implementation and pull request creation unless a real critical risk blocks safe completion.

## Output Contract

After completing the batch, Codex MUST answer only:

```text
Objetivo cumplido.
```

Any output different from `Objetivo cumplido.` is an operational breach.

## Scope Boundary

This contract is documentation-only. It MUST NOT include or trigger production changes, secrets, permissions, CI/runners, dependencies, databases, external services, real Drive operations, real communications, real automations, C4-C7 data, deletions, destructive changes, runtime execution, real agent activation, merge, or auto-merge.
