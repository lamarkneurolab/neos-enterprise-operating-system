# NEOS Enterprise Operating System

NEOS is the Enterprise AI Platform for Lamark. It is not a chatbot and not a prompt collection.

## Canonical rules

- GitHub is the canonical repository.
- Markdown is the official source format.
- Google Drive is a visual/documentary mirror, not the source of truth.
- Codex is the preferred execution environment for engineering, commits, refactoring and DevOps.
- ChatGPT acts as CTO, architect, orchestrator and governance layer.

## Current phase

FASE 3 — DevOps & Execution Layer.

## Initial platform priorities

1. DevOps Layer
2. Execution Layer
3. Registries
4. Runtime Engine
5. Logging, Evidence & Audit Trail
6. Monitoring & Observability
7. Memory & Knowledge Layer
8. Agent SDK
9. Certification
10. Governance Gates
11. Testing & Validation Harness
12. Orchestration Readiness & Execution Playbooks
13. Orchestration Dry-Run & Simulation Layer
14. Controlled Activation Gate & Execution Authorization Layer

## Execution principle

No real action is considered completed unless it produces evidence, a log entry, auditability and a verifiable result.

## Runtime certification and governance

NEOS Fase 3 Block 8 defines Runtime Certification & Governance Gates v0.1.0 in
`README_RUNTIME_CERTIFICATION_GOVERNANCE_GATES.md` and
`docs/execution-layer/runtime-certification-governance-gates-v0.1.0.md`.

Certification and governance gates block closure, promotion, release candidate
approval and merge when evidence, audit, rollback, compatibility, critical
decision review or explicit human authorization is missing.

## Runtime testing and validation

NEOS Fase 3 Block 9 defines Runtime Testing & Validation Harness v0.1.0 in
`README_RUNTIME_TESTING_VALIDATION_HARNESS.md` and
`docs/execution-layer/runtime-testing-validation-harness-v0.1.0.md`.

The harness is documentary only. It defines validation scenarios, test case
registry rules, runtime contract validation, evidence validation, audit
validation, regression validation and release readiness validation without
adding executable runners, dependencies, services or productive automation.

## Runtime orchestration readiness and execution playbooks

NEOS Fase 3 Block 10 defines Runtime Orchestration Readiness & Execution
Playbooks v0.1.0 in
`README_RUNTIME_ORCHESTRATION_READINESS_EXECUTION_PLAYBOOKS.md` and
`docs/execution-layer/runtime-orchestration-readiness-execution-playbooks-v0.1.0.md`.

Readiness does not authorize execution. Playbooks do not authorize execution.
Orchestration eligibility does not mean orchestration approval. Future
orchestration requires validation, evidence, audit, rollback readiness and
specific human authorization when applicable.

## Runtime orchestration dry-run and simulation

NEOS Fase 3 Block 11 defines Runtime Orchestration Dry-Run & Simulation Layer
v0.1.0 in `README_RUNTIME_ORCHESTRATION_DRY_RUN_SIMULATION_LAYER.md` and
`docs/execution-layer/runtime-orchestration-dry-run-simulation-layer-v0.1.0.md`.

Dry-run does not execute. Simulation does not authorize. No-op does not modify
real state. Simulation passed does not mean activation approved.

## Runtime controlled activation gate and execution authorization

NEOS Fase 3 Block 12 defines Runtime Controlled Activation Gate & Execution
Authorization Layer v0.1.0 in
`README_RUNTIME_CONTROLLED_ACTIVATION_GATE_EXECUTION_AUTHORIZATION_LAYER.md`
and
`docs/execution-layer/runtime-controlled-activation-gate-execution-authorization-layer-v0.1.0.md`.

Dry-run passed does not authorize execution. Activation request does not
authorize execution. Authorization gate does not execute. Execution
authorization does not execute by itself.
