# NEOS Runtime Memory & Context Persistence v0.1.0

This document is the operational entry point for NEOS Block 6: Runtime Memory
& Context Persistence.

Block 6 adds the minimum documentary layer for remembering, persisting,
reviewing, resuming and recovering runtime context. It extends Block 3
authorization, Block 4 runtime coordination and Block 5 observability. It does
not create business agents, introduce databases, manage secrets or replace
evidence, audit, incident or rollback logs.

## Objective

Create the minimum runtime memory and context persistence layer for NEOS
Enterprise AI Platform:

- Define Runtime Memory boundaries.
- Register context persistence records.
- Define execution snapshots as auditable checkpoints.
- Define context resume flow.
- Define state recovery rules.
- Classify memory risk levels.
- Link memory records to evidence, decisions, audit, incidents and rollback.
- Define context retention rules.
- Provide a memory review checklist before reusing context.

## Components included

| Component | Purpose |
|---|---|
| Runtime Memory | Defines what runtime context NEOS may or may not remember. |
| Context Persistence | Defines the minimum record for persisted context. |
| Execution Snapshots | Defines auditable execution checkpoints. |
| Context Resume Flow | Defines verification before resuming from memory. |
| State Recovery Rules | Defines how previous operational states may be recovered. |
| Memory Boundaries | Separates valid, temporary, restricted and prohibited memory. |
| Memory Risk Levels | Classifies risk when context is reused. |
| Memory Audit Linkage | Links memory with decisions, evidence, audit, incidents and rollback. |
| Context Retention Rules | Defines how long context may be retained. |
| Memory Review Checklist | Validates persisted context before trust or reuse. |

## Operational flow

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

Runtime Memory records context only as a governed documentary contract.
Context Persistence stores references to already authorized, evidenced and
auditable facts. Execution Snapshots provide checkpoints for resume and
recovery review. None of these components execute work by themselves.

## Files created

| File | Purpose |
|---|---|
| `README_RUNTIME_MEMORY_CONTEXT_PERSISTENCE.md` | Block 6 entry point. |
| `docs/execution-layer/runtime-memory-context-persistence-v0.1.0.md` | Canonical Block 6 specification. |
| `runtime/memory.md` | Runtime memory contract. |
| `runtime/context-persistence.md` | Context persistence contract. |
| `runtime/execution-snapshots.md` | Execution snapshot record contract. |
| `runtime/context-resume.md` | Context resume flow contract. |
| `runtime/state-recovery.md` | State recovery rule contract. |
| `logs/MEMORY_LOG.md` | Runtime memory log template. |
| `logs/CONTEXT_SNAPSHOT_LOG.md` | Context snapshot log template. |

## Files updated

| File | Change |
|---|---|
| `docs/execution-layer/execution-engine.md` | Adds memory, snapshot, resume and recovery closure rules. |
| `docs/execution-layer/runtime-observability-audit-trail-v0.1.0.md` | Adds Block 6 linkage without changing Block 5. |
| `runtime/observability.md` | Adds memory and snapshot inspection references. |
| `runtime/audit-trail.md` | Adds memory audit linkage triggers. |
| `runtime/state-manager.md` | Adds state recovery and snapshot constraints. |
| `logs/DECISION_LOG.md` | Records the Block 6 governance decision. |
| `logs/EVIDENCE_LOG.md` | Records the Block 6 documentary evidence. |
| `logs/AUDIT_TRAIL.md` | Adds Block 6 audit entry. |
| `logs/INCIDENT_LOG.md` | Adds Block 6 initial incident status. |
| `logs/EXECUTION_STATE_LOG.md` | Links Block 6 state evidence. |

## Acceptance criteria

Block 6 v0.1.0 is accepted when:

1. Runtime Memory is documented without creating business agents.
2. Context Persistence is documented without introducing a production database.
3. Execution Snapshots are defined as auditable checkpoints.
4. Context Resume Flow requires verification before resume.
5. State Recovery Rules require evidence and audit linkage.
6. Memory boundaries separate valid, temporary, restricted and prohibited memory.
7. Memory risk levels are documented.
8. Memory is linked to tasks, events, states, evidence, audit, incidents and
   rollback.
9. `logs/MEMORY_LOG.md` is created.
10. `logs/CONTEXT_SNAPSHOT_LOG.md` is created.
11. Existing logs are updated only for necessary cross-references.
12. GitHub remains the canonical source.
13. Markdown `.md` remains the official source format.
14. Google Drive remains a visual/documentary mirror only.
15. No permissions, secrets, dependencies, services or databases are changed.
16. No business, commercial, clinical, documentation, marketing, sales or
   operations agents are created.
17. No automatic merge is performed.

## Initial status v0.1.0

Block 6 v0.1.0 is a documentation and traceability baseline. It establishes
runtime memory and context persistence contracts only. It is not a memory
service, database, vector store, cache, autonomous agent system or production
state recovery engine.

## Restrictions

- GitHub is the canonical source.
- Markdown `.md` is the official source format.
- Google Drive is a visual/documentary mirror only.
- No business agents are created.
- No commercial, clinical, documentation, marketing, sales or operations agents
  are created.
- No automatic merge is performed.
- No permissions are modified.
- No secrets are administered.
- No dependencies are installed.
- No database, external service or production memory store is introduced.
- Memory must not be reused unless it is valid, current, authorized, evidenced
  and auditable.
