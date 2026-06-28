# NEOS + NEXUS Connector Operational Playbooks v0.1.0

## Purpose

These playbooks define how connector work is prepared, operated, escalated, or blocked without activating production, touching sensitive data, or creating uncontrolled external effects. They are designed for documentation-first execution across NEOS and NEXUS.

## Operating stance

The default posture is safe preparation. Operators may inspect approved local context, create documentation, stage non-live artifacts, and prepare handoff evidence. They may not infer permission to use real external accounts, credentials, production systems, restricted data, communications, campaigns, or live automations.

## Common playbook flow

1. Confirm the requested connector class and target boundary.
2. Classify the action as read, draft, write, submit, activate, merge, delete, notify, or schedule.
3. Confirm data class and production status.
4. Select execute, prepare, escalate, or block.
5. Record evidence and safe-stop conditions.
6. Handoff any unresolved authority requirement.

## Shared safe actions

Allowed preparation includes local Markdown documents, mock payloads, dry-run checklists, non-live test plans, branch-local documentation commits, and approval packets. These actions must remain inside the requested path or branch and must not trigger real external effects.

## Shared blocked actions

Blocked actions include production live changes, real secrets, real credentials, unauthorized Drive operations, external communications, live automations, campaigns, C4-C7 data, CI runner activation, dependency installation, merges, auto-merges, and out-of-scope deletion.

## Handoff standard

Every playbook handoff identifies the connector, requested action, target, data class, risk, decision, evidence, blocker if any, and exact authorization needed next.
