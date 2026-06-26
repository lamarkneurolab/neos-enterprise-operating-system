# Runtime Memory & Context Persistence v0.1.0

This is the canonical specification for NEOS Block 6.

Block 6 defines the minimum documentary layer for runtime memory, context
persistence, execution snapshots, context resume, state recovery, memory
boundaries, memory risk levels, audit linkage, retention rules and memory
review.

## Purpose

The purpose of this block is to let NEOS preserve and review operational
context between executions without treating stale, unaudited or unauthorized
context as current truth.

The layer ensures that persisted runtime context has durable references for:

- Authorized decisions.
- Task, event and state records.
- Execution snapshots.
- Evidence entries.
- Audit entries.
- Incident records.
- Rollback references.
- Retention rules.
- Risk classification.

## Scope

Included:

- Runtime Memory contract.
- Context Persistence contract.
- Execution Snapshot records.
- Context Resume Flow.
- State Recovery Rules.
- Memory Boundaries.
- Memory Risk Levels.
- Memory Audit Linkage.
- Context Retention Rules.
- Memory Review Checklist.
- SDK and integration context linkage when contract use persists or reuses
  runtime context.

## Non-goals

Excluded:

- Business agents.
- Commercial, clinical, documentation, marketing, sales or operations agents.
- Autonomous execution.
- Production memory service.
- Database, vector store, cache, worker or external service implementation.
- Permission changes.
- Secret management.
- Dependency installation.
- Automatic merge.

## Runtime placement

Block 6 extends the runtime coordination and observability layers after
authorization, task/event/state coordination and auditability have been
established.

```text
Authorization Flow
  -> Task Queue
  -> Event Bus
  -> State Manager
  -> Runtime Observability
  -> Audit Trail / Incident Records
  -> Runtime Memory / Context Persistence
  -> Execution Snapshots
  -> Context Resume / State Recovery Review
  -> Evidence / Decisions / Rollback
```

Runtime Memory records context boundaries. Context Persistence records
references to governed facts. Execution Snapshots preserve checkpoints. Resume
and recovery are review flows, not automatic execution.

SDK and integration contracts may reference memory only through governed
context records. They must not persist secrets, credentials, tokens,
permissions, stale context, revoked context or unsupported assumptions.

## Runtime Memory Contract

Runtime Memory defines what may be treated as memory inside NEOS runtime
documentation.

| Category | Meaning | Persistence rule |
|---|---|---|
| Operational memory | Current runtime context needed to understand execution. | Persist only with task, state, evidence and audit links. |
| Task memory | Context linked to a specific authorized task. | Persist with `task_id`, `event_id` and `state_id`. |
| Execution memory | Context created while execution is in progress. | Persist through snapshot or discard at closure. |
| Decision memory | Authorized decisions affecting execution. | Persist only with `decision_ref` and authorization. |
| State memory | Current or previous state context. | Persist only with state log linkage. |
| Evidence memory | Evidence references that support runtime facts. | Persist as references, not unverifiable claims. |
| Incident memory | Incident context that affects resume or recovery. | Persist with incident and audit linkage. |
| Rollback memory | Rollback context and recovery constraints. | Persist with evidence and audit linkage. |
| Prohibited memory | Secrets, credentials, tokens, unsupported assumptions or unauthorized sensitive context. | Do not persist as operational truth. |

Runtime Memory must answer:

- What context should NEOS remember?
- What context should NEOS not remember?
- What information requires evidence before persistence?
- What information is temporary?
- What information must be discarded when execution closes?

## Context Persistence Contract

Context Persistence defines the minimum record used to register persisted
context.

| Field | Requirement |
|---|---|
| `context_id` | Unique persisted context identifier. |
| `task_id` | Linked Task Queue identifier. |
| `event_id` | Linked Event Bus identifier. |
| `state_id` | Linked State Manager or execution state identifier. |
| `snapshot_id` | Linked execution snapshot identifier when applicable. |
| `evidence_id` | Linked evidence entry. |
| `audit_id` | Linked audit entry. |
| `incident_id` | Optional linked incident entry. |
| `rollback_id` | Optional rollback reference. |
| `created_at` | Context creation timestamp. |
| `created_by` | Human or runtime governance actor creating the record. |
| `authorized_by` | Authorization source when persistence requires approval. |
| `retention_class` | Context retention class. |
| `risk_level` | Memory reuse risk level. |
| `status` | Context lifecycle status. |

Minimum statuses:

- `draft`
- `active`
- `validated`
- `stale`
- `deprecated`
- `revoked`
- `archived`

## Execution Snapshot Records

Execution Snapshots define auditable checkpoints for runtime execution.

Each snapshot must be able to answer:

- What task was active?
- What state was current?
- What events occurred?
- What decisions were active?
- What evidence existed?
- What authorization was active?
- What risks were open?
- What incidents were linked?
- Whether execution was resumable.
- Whether the snapshot was reliable.

| Field | Requirement |
|---|---|
| `snapshot_id` | Unique snapshot identifier. |
| `execution_id` | Linked execution identifier. |
| `task_id` | Linked task identifier. |
| `state_id` | Linked state identifier. |
| `event_ids` | Linked event identifiers. |
| `decision_ids` | Linked decision identifiers. |
| `evidence_ids` | Linked evidence identifiers. |
| `audit_ids` | Linked audit identifiers. |
| `incident_ids` | Linked incident identifiers when applicable. |
| `rollback_ids` | Linked rollback identifiers when applicable. |
| `created_at` | Snapshot timestamp. |
| `created_by` | Human or runtime governance actor creating the snapshot. |
| `reason` | Reason for creating the snapshot. |
| `resume_allowed` | Whether resume may be considered. |
| `recovery_allowed` | Whether recovery may be considered. |
| `risk_level` | Snapshot reuse risk level. |
| `validation_status` | Current validation status. |

## Context Resume Flow

Context resume requires verification. No execution may resume only because
memory exists.

1. Identify previous execution.
2. Locate the latest valid snapshot.
3. Verify operational state.
4. Verify evidence.
5. Verify audit.
6. Verify open incidents.
7. Confirm memory boundaries.
8. Confirm applicable authorization.
9. Declare context resumable or not resumable.
10. Record the resume decision.

Critical rule:

```text
No execution must resume only because memory exists.
Execution may resume only when memory is valid, traceable, current,
authorized and auditable.
```

## State Recovery Rules

State Recovery defines how previous operational states may be recovered.

| State class | Recovery rule |
|---|---|
| Last stable state | Recover only if evidence and state log agree. |
| Last audited state | Recover only if audit linkage is complete. |
| Last authorized state | Recover only if authorization still applies. |
| Last reliable snapshot | Recover only if snapshot validation is current. |
| Pre-incident state | Recover only after incident review. |
| Pre-rollback state | Recover only for analysis unless rollback is reversed by authorization. |
| Post-rollback state | Recover as current only when rollback evidence is complete. |
| Non-recoverable state | Do not recover when evidence, audit or incident status blocks trust. |

Minimum criterion:

```text
A state may be recovered only when it has sufficient evidence, linked audit
and no critical conflict with open incidents.
```

## Memory Boundaries

NEOS may remember:

- Authorized decisions.
- Operational task state.
- Registered events.
- Validated evidence.
- Approved snapshots.
- Documented incidents.
- Rollback actions.
- Acceptance criteria.
- Active risks.
- Retention rules.

NEOS must not remember as operational truth:

- Unverified assumptions.
- Old instructions contradicted by newer decisions.
- Context without evidence.
- Unauthorized sensitive data.
- Secrets.
- Credentials.
- Tokens.
- Permissions.
- Unnecessary personal information.
- Deleted or unverifiable files.
- Unaudited states.
- Outputs generated without review.

## Memory Risk Levels

| Level | Meaning | Required control |
|---|---|---|
| `low` | Validated, non-sensitive operational context with evidence and audit. | Standard review. |
| `medium` | Useful but partial context, pending review or low operational impact. | Evidence review before reuse. |
| `high` | Context affects decisions, rollback, incidents, integrations or critical states. | Explicit audit and authorization review. |
| `critical` | Sensitive, contradictory, unauthorized or related to secrets, permissions, destructive changes or critical integrations. | Do not reuse until contained and explicitly authorized. |

## Memory Audit Linkage

Persisted memory must link to:

- `logs/DECISION_LOG.md`
- `logs/EVIDENCE_LOG.md`
- `logs/AUDIT_TRAIL.md`
- `logs/INCIDENT_LOG.md`
- `logs/EXECUTION_STATE_LOG.md`
- `logs/MEMORY_LOG.md`
- `logs/CONTEXT_SNAPSHOT_LOG.md`

Minimum rules:

- If memory affects a decision, a decision entry must exist.
- If memory affects execution, state linkage must exist.
- If memory affects rollback, evidence must exist.
- If memory affects an incident, audit linkage must exist.
- If memory is stale, deprecated or revoked, resume must be blocked until
  review.

## Context Retention Rules

| Retention class | Meaning | Reuse rule |
|---|---|---|
| `ephemeral` | Retained only during the current execution. | Discard at closure unless promoted by evidence and authorization. |
| `session` | Retained during one operational session or block. | Revalidate before cross-session reuse. |
| `block` | Retained for one Fase 3 block. | Review at block closure. |
| `phase` | Retained during Fase 3. | Revalidate when later blocks supersede decisions. |
| `permanent` | Canonical rules, critical decisions, approved architecture and official contracts. | Reuse only while not superseded. |
| `restricted` | Sensitive context requiring specific authorization. | Do not persist or reuse without explicit authorization. |

## Memory Review Checklist

Before trusting persisted memory, review:

1. Does it have a unique ID?
2. Does it have a date?
3. Does it have an origin?
4. Is it linked to a task?
5. Is it linked to an event?
6. Is it linked to a state?
7. Does it have evidence?
8. Does it have audit linkage?
9. Does it have a responsible actor?
10. Does it have authorization when applicable?
11. Does it have a risk level?
12. Does it have a retention rule?
13. Is it current?
14. Was it invalidated by a later decision?
15. Is there a related incident?
16. Is there a related rollback?
17. Can execution resume without loss of control?

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

Block 6 v0.1.0 is complete when:

1. Required Block 6 files are created or updated.
2. Runtime Memory contract is documented.
3. Context Persistence contract is documented.
4. Execution Snapshot Records are documented.
5. Context Resume Flow is documented with verification before resume.
6. State Recovery Rules are documented with evidence and audit requirements.
7. Memory Boundaries are documented.
8. Memory Risk Levels are documented.
9. Memory Audit Linkage is documented.
10. Context Retention Rules are documented.
11. Memory Review Checklist is documented.
12. Decision, evidence, execution state, audit, incident, memory and snapshot
    logs are linked.
13. No business agents are created.
14. No destructive changes are introduced.
15. No permissions, secrets, dependencies, databases or services are changed.
16. Validation commands are executed.
17. A non-empty commit is created if implementation is accepted.
18. A Draft PR or PR is opened for human review if authorized.
19. No automatic merge is performed.
