# Runtime SDK & Integration Contracts v0.1.0

This package establishes NEOS Fase 3 Block 7: Runtime SDK & Integration
Contracts v0.1.0.

Block 7 defines the minimum documentary layer for SDK contracts, internal
interfaces, integration contracts, compatibility rules, extension rules,
external execution boundaries, versioning, traceability, audit, risk, evidence
and rollback.

## Purpose

The Runtime SDK provides a documented contract surface for future NEOS modules,
tools, connectors and agents to interact with the Execution Layer without
changing authorization, queue, event, state, observability, audit, memory or
context persistence rules.

Integration Contracts define the allowed entry and exit points between runtime
modules and future external integrations. They do not execute integrations and
do not activate external services.

## Relationship with Blocks 1-6

Block 7 extends the closed Fase 3 baseline:

| Block | Relationship |
|---|---|
| Block 1 - Repository Initialization | Uses GitHub as canonical source and Markdown as official source format. |
| Block 2 - Registry System | Requires capability, permission, tool, connector and runtime registry references before integration use. |
| Block 3 - Runtime Authorization & Execution Flow | Requires authorization before invocation, push, PR, external execution or destructive work. |
| Block 4 - Task Queue, Event Bus & State Manager | Requires task records, events and state transitions for SDK and integration actions. |
| Block 5 - Runtime Observability & Audit Trail | Requires observability, audit and incident linkage for runtime-relevant contract use. |
| Block 6 - Runtime Memory & Context Persistence | Requires governed memory, context, snapshot and recovery linkage when context is persisted or reused. |

Block 7 does not redefine or replace any prior block.

## Included files

| File | Purpose |
|---|---|
| `docs/execution-layer/runtime-sdk-integration-contracts-v0.1.0.md` | Canonical Block 7 specification. |
| `runtime/sdk.md` | Runtime SDK contract set. |
| `runtime/integration-contracts.md` | Integration contract set. |
| `runtime/internal-interfaces.md` | Internal module interface matrix. |
| `runtime/extension-rules.md` | SDK and integration extension rules. |
| `runtime/external-execution-boundaries.md` | Limits for future external execution. |
| `runtime/sdk-versioning.md` | Contract versioning and compatibility rules. |
| `runtime/compatibility-matrix.md` | Compatibility, risk, review and certification matrices. |
| `logs/SDK_CONTRACT_LOG.md` | SDK contract documentary log. |
| `logs/INTEGRATION_CONTRACT_LOG.md` | Integration contract documentary log. |

## Operating limits

Block 7 is documentary only.

It does not create:

- Business agents.
- Commercial, clinical, documentation, marketing, sales or operations agents.
- Production SDK software.
- Databases, workers, services or external connectors.
- Permission changes.
- Secret management.
- Dependency installation.
- External execution.
- Automatic merge.

## Acceptance criteria

- All source content is Markdown.
- GitHub remains the canonical source.
- Google Drive may be used only as a visual or documentary mirror.
- Each SDK contract declares purpose, input, output, precondition,
  postcondition, evidence, audit, risks, rollback and version.
- Each integration contract declares entry point, exit point, operational
  limits, authorization, evidence, audit, failure rule and rollback rule.
- Internal interfaces declare origin, destination, responsibility, allowed data,
  prohibited data, event, state, evidence, risk and control.
- Compatibility, risk, review and certification matrices exist.
- Evidence, audit, state and incident logs are updated when applicable.

## v0.1.0 status

Status: documentary baseline.

Merge status: must remain unmerged until technical review and explicit Tiziano
authorization for the specific pull request.
