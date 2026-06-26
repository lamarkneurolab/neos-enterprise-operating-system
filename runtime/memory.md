# Runtime Memory Contract

The Runtime Memory contract defines the minimum context NEOS may remember
between runtime execution steps.

The v0.1.0 memory layer is documentary. It records memory boundaries and links
memory to evidence, audit, state, incidents and rollback. It does not create a
memory service, database, vector store, cache or autonomous agent.

## Purpose

Runtime Memory makes operational context reusable only when it is governed
across authorization outcomes, Task Queue records, Event Bus events, State
Manager transitions, observability events, evidence entries, audit entries,
incident records, rollback references and execution snapshots.

## Memory categories

| Category | Requirement |
|---|---|
| `operational_memory` | Current execution context with task, state, evidence and audit links. |
| `task_memory` | Context tied to a single authorized task. |
| `execution_memory` | Context created during execution and closed, discarded or snapshotted. |
| `decision_memory` | Authorized decisions with decision log linkage. |
| `state_memory` | Current or previous state context with state log linkage. |
| `evidence_memory` | Evidence references that support runtime facts. |
| `incident_memory` | Incident context that may block resume or recovery. |
| `rollback_memory` | Rollback context and recovery constraints. |
| `prohibited_memory` | Context that must not be persisted as operational truth. |

## Valid memory

NEOS may remember:

- Authorized decisions.
- Operational task states.
- Registered events.
- Validated evidence.
- Approved snapshots.
- Documented incidents.
- Rollback actions.
- Acceptance criteria.
- Active risks.
- Retention rules.

## Temporary memory

Temporary context may be used during an active execution but must be discarded
or explicitly promoted through evidence and audit before closure.

Temporary memory includes:

- Draft execution notes.
- Unverified observations.
- Intermediate command output.
- Local assumptions pending validation.
- Partial task context not yet linked to state.

## Prohibited memory

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

## Rules

- Runtime Memory must not authorize, execute, rollback or mutate state by
  itself.
- Memory affecting decisions must link a decision record.
- Memory affecting execution must link task, event and state records.
- Memory affecting rollback must link evidence.
- Memory affecting incidents must link audit.
- Stale, deprecated or revoked memory must not be reused without review.
- Restricted memory requires explicit authorization before persistence or reuse.
- SDK and integration contract use may reference memory only when context is
  validated, current, evidenced and audited.
- SDK and integration contract use must not persist secrets, credentials,
  tokens, permissions, stale context, revoked context or unsupported
  assumptions.

## Non-goals

- No production memory store is introduced.
- No database, cache or vector index is introduced.
- No business agent memory is created.
- No secret, credential, token or permission is persisted.
