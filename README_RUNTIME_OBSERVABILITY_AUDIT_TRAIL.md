# NEOS Runtime Observability & Audit Trail v0.1.0

This document is the operational entry point for NEOS Block 5: Runtime
Observability & Audit Trail.

Block 5 adds the minimum documentary layer for observing, auditing and
reviewing runtime execution. It complements Block 3 authorization and Block 4
runtime coordination. It does not execute actions by itself, create business
agents, introduce workers or replace the Event Bus, State Manager or evidence
logs.

## Objective

Create the minimum runtime observability and audit trail layer for NEOS
Enterprise AI Platform:

- Record runtime observability events.
- Register operational audit entries.
- Track runtime health signals.
- Record incident records.
- Inspect events without replacing the Block 4 Event Bus.
- Define execution metrics for review.
- Link evidence, decisions, state transitions, incidents and rollback.

## Components included

| Component | Purpose |
|---|---|
| Runtime Observability | Records, classifies and inspects runtime events. |
| Audit Trail | Records governance-relevant runtime actions. |
| Health Signals | Declares minimal operational health status. |
| Incident Records | Records runtime failures, blocked conditions and manual intervention needs. |
| Event Inspection | Adds searchable inspection fields to Event Bus records. |
| Execution Metrics | Defines counters used for operational review. |
| Runtime Review Checklist | Validates execution completeness before closure. |

## Operational flow

```text
Authorization Flow
  -> Task Queue
  -> Event Bus
  -> State Manager
  -> Runtime Observability
  -> Audit Trail / Incident Records
  -> Execution State Log
  -> Evidence / Decisions / Rollback
```

Observability records and classifies runtime facts. Audit Trail records
governance-relevant actions. Incident Records capture blocked, failed or risky
conditions. None of these components execute business actions by themselves.

## Files created

| File | Purpose |
|---|---|
| `README_RUNTIME_OBSERVABILITY_AUDIT_TRAIL.md` | Block 5 entry point. |
| `docs/execution-layer/runtime-observability-audit-trail-v0.1.0.md` | Canonical Block 5 specification. |
| `runtime/observability.md` | Runtime observability contract. |
| `runtime/audit-trail.md` | Audit trail contract. |
| `runtime/health-signals.md` | Health signal contract. |
| `runtime/incident-records.md` | Incident record contract. |
| `logs/INCIDENT_LOG.md` | Incident log template. |

## Files updated

| File | Change |
|---|---|
| `docs/execution-layer/execution-engine.md` | Adds observability, audit and incident closure rules. |
| `docs/execution-layer/task-queue-event-bus-state-manager-v0.1.0.md` | Adds Block 5 linkage without replacing Block 4. |
| `runtime/event-bus.md` | Adds event inspection fields. |
| `runtime/state-manager.md` | Adds observability and incident transition notes. |
| `logs/AUDIT_TRAIL.md` | Adds Block 5 audit entry template. |
| `logs/EXECUTION_STATE_LOG.md` | Links Block 5 state evidence. |
| `logs/DECISION_LOG.md` | Records the Block 5 governance decision. |
| `logs/EVIDENCE_LOG.md` | Records the Block 5 documentary evidence. |

## Acceptance criteria

Block 5 v0.1.0 is accepted when:

1. Runtime observability, audit trail, health signals and incident records are
   documented.
2. Event inspection complements the Block 4 Event Bus.
3. Execution metrics are defined.
4. Runtime review checklist is documented.
5. Decision, evidence, execution state, audit and incident logs are linked.
6. No business agents are created.
7. No production workers are introduced.
8. No permission, secret or dependency changes are introduced.
9. Validation commands are executed.
10. A Draft PR is opened for human review.
11. No automatic merge is performed.

## Initial status v0.1.0

Block 5 v0.1.0 is a documentation and traceability baseline. It establishes
runtime observability and audit contracts only. It is not an autonomous
execution engine and does not provide monitoring infrastructure, persistent
storage, dashboards, workers or external service integration.

## Restrictions

- GitHub is the canonical source.
- Markdown `.md` is the official source format.
- No business agents are created.
- No commercial, clinical, documentation, marketing, sales or operations agents
  are created.
- No automatic merge is performed.
- No permissions are modified.
- No secrets are administered.
- No dependencies are installed.
- Every execution must preserve evidence, audit, incident and rollback
  traceability.
