# Automation Connector Playbook

## Allowed preparation

Automation preparation may define triggers, mock schedules, dry-run payloads, disablement procedures, monitoring checklists, and rollback plans. Prepared artifacts must not register live jobs or schedule external execution.

## Execute boundary

Automation execution requires named environment, trigger, cadence, end condition, owner, maximum frequency, affected systems, rollback procedure, monitoring expectation, and explicit activation approval.

## Required checks

Confirm that the automation is bounded, reversible, observable, owned by a human, and unable to expand its own permissions or create unbounded downstream actions.

## Escalation triggers

Escalate when the automation has no end condition, unclear blast radius, unknown owner, missing disablement path, dependency on production credentials, or ability to send, publish, spend, delete, merge, or modify external systems.

## Block conditions

Block live automations without explicit authorization, self-modifying workflows, unbounded recurrence, hidden notifications, production mutations, campaign activation, secret handling, and unsupervised external writes.

## Handoff evidence

The automation handoff records trigger, schedule, owner, target systems, data class, stop condition, monitoring signals, rollback procedure, and activation authorization gap.
