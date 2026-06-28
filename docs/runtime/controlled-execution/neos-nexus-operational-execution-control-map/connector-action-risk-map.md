# Connector Action Risk Map

## Purpose

This map classifies connector actions by operational risk so NEOS/NEXUS can decide quickly whether to execute, prepare, escalate, or block.

## Risk Map

| Action | Risk posture | Required decision |
| --- | --- | --- |
| Read approved public or local documentation | Low | Execute when in scope. |
| Draft local Markdown, review packet, mock payload, or handoff | Low | Prepare when no live effect exists. |
| Read connector metadata from an approved account | Medium | Execute only when connector, account, object, and data class are authorized. |
| Write to repository branch or PR body | Medium | Execute only within exact repo, branch, path, and PR scope. |
| Submit, send, publish, share, schedule, or notify | High | Require exact approval of destination, identity, payload, timing, and evidence. |
| Activate campaign, automation, live agent, serving, billing, or production runtime | Critical | Require exact activation approval, owner, stop condition, monitoring, and rollback. |
| Merge or auto-merge | Critical | Require PR number, exact Head SHA, base branch, validation evidence, and explicit merge approval. |
| Permission, secret, credential, deletion, Drive mutation, or C4-C7 data action | Critical | Block unless exact policy-valid authorization and evidence are present. |

## Risk Shortcut

If the action can change a real external state or expose sensitive material, treat it as high or critical until proven otherwise.
