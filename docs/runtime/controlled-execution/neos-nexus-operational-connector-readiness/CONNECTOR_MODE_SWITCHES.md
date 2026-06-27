# Connector Mode Switches

## Purpose

Connector mode switches define how NEOS/NEXUS moves from documentation to controlled action without confusing technical capability with operational authorization.

Each connector must declare its current mode before use. A higher mode cannot be assumed from a lower mode.

## Modes

| Mode | Name | Meaning | Block 28 Status |
| --- | --- | --- | --- |
| MODE_0_DOCUMENTATION_ONLY | Documentation only | The connector is described, mapped, or designed, but not used against live systems. | Allowed. |
| MODE_1_READ_ONLY | Read only | The connector may read authorized, non-sensitive data within a defined scope. | Allowed only if access and scope are already authorized. |
| MODE_2_DRAFT_PREPARATION | Draft preparation | The connector may prepare drafts, plans, scripts, proposed records, or messages without executing them live. | Allowed for internal and non-sensitive work. |
| MODE_3_CONTROLLED_EXECUTION | Controlled execution | The connector may perform scoped, reversible, non-critical actions such as branch, commit, push, PR, local validation, or internal non-sensitive document creation. | Allowed only for explicitly scoped tasks. |
| MODE_4_HUMAN_APPROVED_CRITICAL_ACTION | Human-approved critical action | A critical action may be performed only after Tiziano or the applicable authority approves the exact action, scope, and target. | Available as a governance state, but not invoked automatically. |
| MODE_5_LIVE_AUTOMATION_PRODUCTION | Live automation production | The connector can act in production through live triggers, agents, campaigns, external communications, financial workflows, or operational automations. | Blocked in Block 28. |

## Transition Criteria

| Transition | Criteria |
| --- | --- |
| MODE_0 to MODE_1 | The tool exists, the access path is known, the data scope is authorized, and the data classification is C0-C3 unless explicit approval covers higher classes. |
| MODE_1 to MODE_2 | Reading is authorized and the requested output is a non-live draft, internal artifact, or proposed action. |
| MODE_2 to MODE_3 | The action is scoped, non-destructive, reversible or reviewable, and does not affect external parties, production, money, permissions, secrets, or C4-C7 data. |
| MODE_3 to MODE_4 | The action is critical but has a specific human approval with exact target, action, and expected impact. |
| MODE_4 to MODE_5 | Requires separate production authorization, connector readiness review, logging controls, rollback plan, owner assignment, and explicit approval. This transition is blocked in Block 28. |

## Mode Guardrails

- MODE_0 never grants data access.
- MODE_1 never grants write or send authority.
- MODE_2 never grants execution authority.
- MODE_3 never grants critical-action authority.
- MODE_4 never implies recurring production authority.
- MODE_5 is not authorized in Block 28.

## Block 28 Lock

MODE_5_LIVE_AUTOMATION_PRODUCTION remains blocked for this block.

No live connector, live agent, production workflow, campaign, external communication, billing flow, or automated execution may be activated through Block 28.
