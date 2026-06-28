# Codex Output Contract v0.1.0

## Final Response

When the bounded documentary block is complete, Codex MUST respond with exactly:

```text
Objetivo cumplido.
```

## Breach Rule

Any final response different from `Objetivo cumplido.` is an operational breach.

This includes extra summaries, links, metadata, explanations, caveats, validation tables, pull request descriptions, or continuation prompts in the chat response.

## Audit Timing

The assistant MUST audit the pull request directly after opening it.

The audit result is part of the execution obligation, but it MUST NOT expand the final chat response beyond:

```text
Objetivo cumplido.
```

## Non-Execution Boundary

The output contract does not authorize production actions, secrets handling, permission changes, CI/runner changes, dependency changes, database changes, external service operations, real Drive operations, real communications, real automations, C4-C7 data handling, deletions, destructive changes, runtime execution, real agent activation, merge, or auto-merge.
