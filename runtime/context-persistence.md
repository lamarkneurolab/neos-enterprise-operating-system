# Context Persistence Contract

The Context Persistence contract defines the minimum record used to preserve
runtime context between NEOS executions.

The v0.1.0 persistence layer is documentary. It records references to governed
facts and does not implement a production database, cache, vector store or
external service.

## Purpose

Context Persistence preserves a reviewable path between Runtime Memory records,
Task Queue records, Event Bus events, State Manager records, execution
snapshots, decisions, evidence, audit, incidents and rollback references.

## Minimum context record

| Field | Requirement |
|---|---|
| `context_id` | Required unique persisted context identifier. |
| `task_id` | Linked Task Queue identifier. |
| `event_id` | Linked Event Bus identifier. |
| `state_id` | Linked State Manager or execution state identifier. |
| `snapshot_id` | Linked execution snapshot identifier when applicable. |
| `evidence_id` | Linked evidence entry. |
| `audit_id` | Linked audit entry. |
| `incident_id` | Optional incident entry. |
| `rollback_id` | Optional rollback reference. |
| `created_at` | Required creation timestamp. |
| `created_by` | Human or runtime governance actor creating the record. |
| `authorized_by` | Authorization source when persistence requires approval. |
| `retention_class` | Retention class controlling lifetime and reuse. |
| `risk_level` | Memory reuse risk level. |
| `status` | Current context status. |

## Status values

| Status | Meaning |
|---|---|
| `draft` | Context captured but not validated. |
| `active` | Context may be considered during the current execution. |
| `validated` | Context has evidence and audit linkage. |
| `stale` | Context may be outdated and requires review. |
| `deprecated` | Context is superseded by a newer decision or record. |
| `revoked` | Context must not be reused. |
| `archived` | Context retained for history, not active use. |

## Retention classes

| Retention class | Requirement |
|---|---|
| `ephemeral` | Retain only during current execution. |
| `session` | Retain during one operational session or block. |
| `block` | Retain during one Fase 3 block. |
| `phase` | Retain during Fase 3. |
| `permanent` | Retain only for canonical rules, critical decisions and approved contracts. |
| `restricted` | Retain or reuse only with explicit authorization. |

## Rules

- Context must not be persisted without a unique `context_id`.
- Medium, high and critical context must link evidence and audit.
- Context with an open critical incident must not be marked `validated`.
- Context contradicted by a later decision must be marked `deprecated` or
  `revoked`.
- Prohibited memory must not be represented as valid context.
- SDK and integration context references must include the relevant contract id
  when contract use affects resume, recovery, rollback, audit or evidence.
- External execution context must not be persisted as valid context in Block 7
  because real external execution is out of scope.

## Non-goals

- No database schema is introduced.
- No external persistence service is introduced.
- No automated long-term retention system is introduced.
