# Codex Operational Enforcement Layer v0.1.0

## Purpose

This layer converts the Codex Ultra Compact Execution Contract into minimum PR-time controls. It adds no new doctrine, runtime, automation, agent, permission, CI, or external service behavior.

## Enforcement Set

| Control | File | Use |
| --- | --- | --- |
| PR audit checklist | `pr-audit-ultra-compact-checklist.md` | Confirm scope, evidence, PR state, and blocked actions before closure. |
| Output contract verifier | `codex-output-contract-manual-verifier.md` | Manually verify the final Codex response contract. |
| Human authorization guide | `human-pr-merge-authorization-guide.md` | Confirm merge remains human-only and SHA-specific. |

## Source Contract

This layer operationalizes:

- `docs/runtime/controlled-execution/codex-ultra-compact-execution-contract/codex-ultra-compact-execution-contract.md`
- `docs/runtime/controlled-execution/codex-ultra-compact-execution-contract/codex-output-contract.md`
- `docs/runtime/controlled-execution/codex-ultra-compact-execution-contract/human-merge-authorization-boundary.md`

## Stop Rule

If a proposed change expands this layer into repeated doctrine, runtime behavior, real agents, automation, or external execution, stop the PR and leave it unmerged.
