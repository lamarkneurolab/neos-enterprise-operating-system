# Safe Execution Handoff Playbook

## Purpose

The safe execution handoff converts prepared work into a reviewable package without granting live authority. It is used when a connector action is ready for human review, escalation, or later execution.

## Handoff contents

The package includes objective, connector class, target, branch or document path, action type, data class, risk tier, prepared artifacts, validation evidence, known blockers, and exact authorization required for any next execution step.

## Safe wording

Handoffs distinguish prepared from executed work. They avoid language that implies production activation, live send, live automation, campaign launch, merge, or external write when those actions have not been authorized.

## Authorization requirements

Execution handoff must ask for exact scope. Merge handoff must require individual PR number and exact Head SHA. Automation handoff must require owner, cadence, end condition, and rollback. Communication handoff must require final content, channel, sender, and recipient list.

## Stop conditions

The handoff stops before any live effect if authorization is missing, data class is uncertain, scope differs from the prepared artifact, or the approver attempts to authorize a batch merge without individual identifiers.

## Completion standard

A handoff is complete when a reviewer can approve, reject, or request changes without needing hidden context, real credentials, restricted data excerpts, or unrecorded connector state.
