# Runtime Observability & Audit Trail v0.1.0

This is the canonical specification for NEOS Block 5.

Block 5 defines the minimum documentary layer for runtime observability,
operational audit, health signals, incident records, event inspection,
execution metrics and runtime review.

## Purpose

The purpose of this block is to make runtime execution inspectable and
auditable after Block 3 authorization and Block 4 coordination have established
the authorized task, event and state lifecycle.

The layer ensures that runtime execution has durable references for:

- Observability events.
- Audit entries.
- Health signals.
- Incident records.
- Event inspection.
- Execution metrics.
- Evidence linkage.
- Decision linkage.
- Rollback linkage.
- Runtime memory and context snapshot linkage when execution context is
  persisted or reused.

## Scope

Included:

- Runtime Observability contract.
- Audit Trail contract.
- Health Signals contract.
- Incident Records contract.
- Event Inspection fields.
- Execution Metrics.
- Runtime Review Checklist.
- Required links to decisions, evidence, state transitions, events and rollback.
- SDK and integration contract observability linkage.

## Non-goals

Excluded:

- Business agents.
- Commercial, clinical, documentation, marketing, sales or operations agents.
- Autonomous execution.
- Monitoring vendor implementation.
- Database, queue, dashboard or worker implementation.
- Permission changes.
- Secret management.
- Dependency installation.
- Automatic merge.

## Runtime placement

Block 5 extends the runtime coordination layer after authorization and during
state-managed execution.

```text
Authorization Flow
  -> Task Queue
  -> Event Bus
  -> State Manager
  -> Runtime Observability
  -> Audit Trail / Incident Records
  -> Runtime SDK / Integration Contract Review
  -> Execution State Log
  -> Evidence / Decisions / Rollback
```

Runtime Observability records, classifies and inspects. It does not execute
actions by itself. Audit Trail records governance-relevant operational facts.
Incident Records preserve failure, degraded or blocked conditions.

SDK and integration contract review is observable and auditable when it affects
runtime governance, compatibility, external execution boundaries, evidence or
rollback.

## Runtime Observability

Runtime Observability defines the minimum record used to inspect runtime
behavior.

Required fields:

| Field | Requirement |
|---|---|
| `observability_event_id` | Unique observability event identifier. |
| `timestamp` | Event observation timestamp. |
| `runtime_component` | Component being observed. |
| `task_id` | Linked task identifier when applicable. |
| `event_type` | Runtime event taxonomy value or inspection category. |
| `state_before` | State before the observed event when applicable. |
| `state_after` | State after the observed event when applicable. |
| `severity` | Informational, warning, error or critical severity. |
| `risk_level` | Low, medium, high or critical runtime risk. |
| `evidence_ref` | Evidence log reference. |
| `audit_ref` | Audit trail reference. |
| `incident_ref` | Incident log reference when applicable. |
| `rollback_ref` | Rollback reference when applicable. |

Rules:

- Observability records runtime facts for inspection.
- Observability must not authorize, execute, retry, rollback or mutate state by
  itself.
- Observability must link evidence for medium, high and critical runtime events.
- Observability must link audit when governance-relevant action is recorded.
- Observability must link incident records for failed, blocked, degraded or
  manual intervention conditions.

## Audit Trail

Audit Trail defines the minimum record used to audit runtime actions and
governance-relevant events.

Required fields:

| Field | Requirement |
|---|---|
| `audit_id` | Unique audit entry identifier. |
| `timestamp` | Audit entry timestamp. |
| `runtime_component` | Runtime component responsible for the action. |
| `task_id` | Linked task identifier when applicable. |
| `event_id` | Linked Event Bus event identifier. |
| `action` | Audited action or governance-relevant event. |
| `authorization_ref` | Authorization reference from Block 3. |
| `decision_ref` | Decision log reference. |
| `evidence_ref` | Evidence log reference. |
| `incident_ref` | Incident log reference when applicable. |
| `rollback_ref` | Rollback reference when applicable. |
| `result` | Action result. |
| `risk_level` | Low, medium, high or critical runtime risk. |
| `notes` | Human-readable context. |

Required log links:

- `logs/DECISION_LOG.md`
- `logs/EVIDENCE_LOG.md`
- `logs/EXECUTION_STATE_LOG.md`
- `logs/AUDIT_TRAIL.md`
- `logs/INCIDENT_LOG.md`

## Health Signals

Health Signals define the minimum runtime readiness and integrity checks.

Required signals:

| Signal | Meaning |
|---|---|
| `runtime.available` | Runtime documentation and execution context are available. |
| `queue.accepting_tasks` | Task Queue contract can accept authorized task records. |
| `event_bus.accepting_events` | Event Bus contract can accept event records. |
| `state_manager.validating_transitions` | State Manager can validate transitions. |
| `audit_trail.writable` | Audit Trail can record entries. |
| `evidence_log.available` | Evidence Log can record or reference evidence. |
| `incident_log.available` | Incident Log can record incidents. |
| `rollback_hooks.available` | Rollback hooks can be evaluated and referenced. |

Minimum statuses:

- `healthy`
- `degraded`
- `blocked`
- `failed`
- `unknown`

## Incident Records

Incident Records define the minimum record for runtime conditions that require
containment, review, rollback or manual intervention.

Minimum incident types:

- `unauthorized_execution_attempt`
- `invalid_state_transition`
- `missing_evidence`
- `missing_audit_entry`
- `event_dispatch_failure`
- `rollback_failure`
- `task_stuck`
- `runtime_component_unavailable`
- `manual_intervention_required`

Required fields:

| Field | Requirement |
|---|---|
| `incident_id` | Unique incident identifier. |
| `timestamp` | Incident detection timestamp. |
| `severity` | Informational, warning, error or critical severity. |
| `affected_component` | Runtime component affected by the incident. |
| `task_id` | Linked task identifier when applicable. |
| `event_id` | Linked Event Bus event identifier when applicable. |
| `description` | Human-readable incident summary. |
| `detected_by` | Human, runtime component or review process that detected it. |
| `risk_level` | Low, medium, high or critical runtime risk. |
| `containment_action` | Immediate containment or stop condition. |
| `rollback_required` | `true`, `false` or `not_required`. |
| `rollback_ref` | Rollback reference when applicable. |
| `evidence_ref` | Evidence log reference. |
| `audit_ref` | Audit trail reference. |
| `status` | Current incident status. |

Minimum statuses:

- `open`
- `triaged`
- `contained`
- `resolved`
- `rollback_required`
- `closed`

## Event Inspection

Event Inspection complements the Block 4 Event Bus. It does not replace the
Event Bus, change its taxonomy or add a production event transport.

Runtime event records should be inspectable by:

- `event_id`
- `event_type`
- `task_id`
- `runtime_component`
- `severity`
- `timestamp`
- `state_transition`
- `audit_ref`
- `evidence_ref`
- `incident_ref`

## Execution Metrics

Execution Metrics define minimum counters for runtime review.

Required metrics:

- `tasks_created`
- `tasks_authorized`
- `tasks_blocked`
- `tasks_started`
- `tasks_completed`
- `tasks_failed`
- `rollbacks_requested`
- `rollbacks_completed`
- `incidents_opened`
- `incidents_resolved`
- `audit_entries_created`
- `evidence_entries_created`
- `invalid_transitions_blocked`

Metrics are documentary counters for review. They do not imply automated
telemetry, dashboards or external monitoring.

## Runtime Review Checklist

Before an execution is considered closed, review:

1. Was the task authorized?
2. Was the state transition valid?
3. Was the event recorded?
4. Was evidence created?
5. Was audit recorded?
6. Was there an incident?
7. Was there a rollback?
8. Is the final state coherent?
9. Was the log updated?

## Required link model

| Source | Required links |
|---|---|
| Observability event | Evidence, audit, incident and rollback references when applicable. |
| Audit entry | Authorization, decision, evidence, incident and rollback references. |
| Incident record | Event, evidence, audit and rollback references. |
| State transition | Event, evidence, audit and incident references when applicable. |
| Rollback hook | Evidence, audit and incident references when applicable. |
| Memory record | Decision, evidence, audit, incident, state and snapshot references when applicable. |
| Context snapshot | Task, event, state, decision, evidence, audit, incident and rollback references. |

## Block 6 linkage

Block 6 Runtime Memory & Context Persistence extends this observability and
audit layer with:

- `runtime/memory.md`
- `runtime/context-persistence.md`
- `runtime/execution-snapshots.md`
- `runtime/context-resume.md`
- `runtime/state-recovery.md`
- `logs/MEMORY_LOG.md`
- `logs/CONTEXT_SNAPSHOT_LOG.md`

Observability and audit records remain the source of inspection and governance
links. Memory and snapshots must not replace evidence, audit, incident or
rollback records.

## Verification

Minimum verification for this documentation block:

```text
git status -sb
git diff --check
git diff --stat
git log --oneline --decorate -n 5
```

If `markdownlint` is available, run:

```text
markdownlint .
```

## Acceptance criteria

Block 5 v0.1.0 is complete when:

1. Required Block 5 files are created or updated.
2. Runtime Observability contract is documented.
3. Audit Trail contract is documented.
4. Health Signals contract is documented.
5. Incident Records contract is documented.
6. Event Inspection complements the Block 4 Event Bus.
7. Execution Metrics are documented.
8. Runtime Review Checklist is documented.
9. Decision, evidence, execution state, audit and incident logs are linked.
10. No business agents are created.
11. No destructive changes are introduced.
12. Validation commands are executed.
13. A non-empty commit is created.
14. A Draft PR is opened for human review.
15. No automatic merge is performed.

## Block 8 certification linkage

Block 8 adds audit sufficiency and governance gate review over runtime
observability and audit trail work.

Any observability or audit change that affects runtime governance must pass:

- `runtime/audit-sufficiency-rules.md`
- `runtime/evidence-sufficiency-rules.md`
- `runtime/governance-gate-matrix.md`
- `runtime/pre-merge-governance-review.md`

Missing audit for a governance-relevant action blocks closure and merge until
the audit entry links action, authorization, decision, evidence, incident and
rollback context when applicable.
