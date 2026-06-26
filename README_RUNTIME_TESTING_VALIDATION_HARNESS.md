# Runtime Testing & Validation Harness v0.1.0

This package establishes NEOS Fase 3 Block 9: Runtime Testing & Validation
Harness v0.1.0.

Block 9 defines the documentary testing and validation layer for NEOS runtime
work. It does not introduce executable test frameworks, runners, services,
databases, external integrations or productive automations.

## Purpose

The Runtime Testing & Validation Harness defines how runtime validation is
designed, documented, reviewed, evidenced, audited, blocked, rolled back and
linked to certification and governance gates.

## Relationship with Blocks 1-8

| Block | Relationship |
|---|---|
| Block 1 - Repository Initialization | Preserves GitHub as canonical source and Markdown as official source format. |
| Block 2 - Registry System | Validates references to capabilities, permissions, tools, connectors and runtimes. |
| Block 3 - Runtime Authorization & Execution Flow | Validates authorization required, missing, denied, expired and merge-specific authorization states. |
| Block 4 - Task Queue, Event Bus & State Manager | Validates task, event and state lifecycle behavior. |
| Block 5 - Runtime Observability & Audit Trail | Validates visibility, audit traceability and incident evidence. |
| Block 6 - Runtime Memory & Context Persistence | Validates memory, context, snapshots, resume and recovery constraints. |
| Block 7 - Runtime SDK & Integration Contracts | Validates SDK, integration, interface, boundary, extension, versioning and compatibility contracts. |
| Block 8 - Runtime Certification & Governance Gates | Validates certification gates, governance gates, readiness, evidence and audit sufficiency. |

Block 9 is additive. It does not replace or weaken any prior block.

## Included files

| File | Purpose |
|---|---|
| `docs/execution-layer/runtime-testing-validation-harness-v0.1.0.md` | Canonical Block 9 specification. |
| `runtime/testing-harness.md` | Runtime testing harness model. |
| `runtime/validation-scenarios.md` | Validation scenario model. |
| `runtime/test-case-registry.md` | Test case registry rules. |
| `runtime/runtime-contract-validation.md` | Runtime contract validation. |
| `runtime/authorization-flow-validation.md` | Authorization flow validation. |
| `runtime/execution-flow-validation.md` | Execution flow validation. |
| `runtime/task-queue-validation.md` | Task queue validation. |
| `runtime/event-bus-validation.md` | Event bus validation. |
| `runtime/state-manager-validation.md` | State manager validation. |
| `runtime/observability-validation.md` | Observability validation. |
| `runtime/audit-trail-validation.md` | Audit trail validation. |
| `runtime/memory-context-validation.md` | Memory and context validation. |
| `runtime/sdk-contract-validation.md` | SDK contract validation. |
| `runtime/integration-contract-validation.md` | Integration contract validation. |
| `runtime/certification-gate-validation.md` | Certification gate validation. |
| `runtime/governance-gate-validation.md` | Governance gate validation. |
| `runtime/rollback-validation.md` | Rollback validation. |
| `runtime/failure-scenario-validation.md` | Failure scenario validation. |
| `runtime/evidence-validation.md` | Evidence validation. |
| `runtime/audit-validation.md` | Audit validation. |
| `runtime/regression-validation.md` | Regression validation. |
| `runtime/release-readiness-validation.md` | Release readiness validation. |
| `logs/TEST_CASE_REGISTRY_LOG.md` | Test case registry log template. |
| `logs/VALIDATION_LOG.md` | Validation log template. |
| `logs/TEST_EVIDENCE_LOG.md` | Test evidence log template. |
| `logs/REGRESSION_REVIEW_LOG.md` | Regression review log template. |
| `logs/RELEASE_READINESS_VALIDATION_LOG.md` | Release readiness validation log template. |

## Operating limits

Block 9 is documentary only.

It does not create:

- Business agents.
- Commercial, clinical, documentation, marketing, sales or operations agents.
- Executable test framework, runner or CI automation.
- Production databases, services, workers or queues.
- External integrations or external service activation.
- Permission changes.
- Secret management.
- Dependency installation.
- File deletion or destructive changes.
- Automatic merge.

## Acceptance criteria

- All new files are Markdown `.md`.
- The harness remains documentary v0.1.0.
- Runtime validation scenarios and test cases link to evidence, audit,
  rollback, certification gates and governance gates.
- Release readiness validation is defined.
- Logs for test cases, validation, test evidence, regression and release
  readiness exist as Markdown templates.
- `git diff --check` passes.
- Pull request is opened against `main`.
- No merge is executed without explicit Tiziano authorization for the specific
  PR.
