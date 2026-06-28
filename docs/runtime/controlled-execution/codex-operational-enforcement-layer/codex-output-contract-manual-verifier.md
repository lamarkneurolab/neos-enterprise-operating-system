# Codex Output Contract Manual Verifier v0.1.0

## Verification Steps

1. Confirm the requested block was bounded to documentary or allowed lightweight configuration changes.
2. Confirm implementation, scope validation, commit, push, PR creation, and direct PR audit were completed.
3. Confirm the final chat response contains exactly:

```text
Objetivo cumplido.
```

## Non-Compliant Output

The final response is non-compliant if it adds summaries, links, caveats, metadata, test notes, PR details, continuation prompts, or any text beyond the exact required sentence.

## Manual Evidence

Record verification in the PR description by checking the Codex Operational Enforcement section and including the current PR URL and Head SHA.
