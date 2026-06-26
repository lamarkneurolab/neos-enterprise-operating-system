# Runtime Certification & Governance Gates v0.1.0

This package establishes NEOS Fase 3 Block 8: Runtime Certification &
Governance Gates v0.1.0.

Block 8 defines the documentary control layer used to certify whether runtime
work is valid, promotable, closable, integrable, rollback-ready, audit-ready and
human-authorized.

## Purpose

Certification and governance gates prevent NEOS execution-layer work from
closing when evidence, audit, rollback, compatibility or human authorization is
missing.

Block 8 does not execute processes. It defines mandatory review gates across
Authorization Flow, Execution Flow, Task Queue, Event Bus, State Manager,
Observability, Audit Trail, Runtime Memory, Context Persistence, SDK Contracts,
Integration Contracts, Rollback, Evidence and Release Candidate Review.

## Relationship with Blocks 1-7

| Block | Relationship |
|---|---|
| Block 1 - Repository Initialization | Preserves GitHub as canonical source and Markdown as official source format. |
| Block 2 - Registry System | Requires registry references before certification of governed runtime work. |
| Block 3 - Runtime Authorization & Execution Flow | Adds certification gates after authorization and before closure or merge. |
| Block 4 - Task Queue, Event Bus & State Manager | Requires task, event and state traceability for governed outcomes. |
| Block 5 - Runtime Observability & Audit Trail | Defines audit sufficiency and governance review requirements. |
| Block 6 - Runtime Memory & Context Persistence | Defines memory and context certification constraints. |
| Block 7 - Runtime SDK & Integration Contracts | Adds readiness gates for SDK, integration, compatibility and external boundaries. |

Block 8 is additive. It does not replace or weaken any prior block.

## Included files

| File | Purpose |
|---|---|
| `docs/execution-layer/runtime-certification-governance-gates-v0.1.0.md` | Canonical Block 8 specification. |
| `runtime/certification-gates.md` | Certification gate catalog. |
| `runtime/governance-gate-matrix.md` | Governance matrix by change type and risk. |
| `runtime/pre-merge-governance-review.md` | Required review before PR merge. |
| `runtime/runtime-compliance-checklist.md` | Runtime compliance checklist for PR and block closure. |
| `runtime/execution-readiness-certification.md` | Execution readiness certification. |
| `runtime/integration-readiness-certification.md` | Integration readiness certification. |
| `runtime/rollback-readiness-certification.md` | Rollback readiness certification. |
| `runtime/evidence-sufficiency-rules.md` | Evidence sufficiency rules. |
| `runtime/audit-sufficiency-rules.md` | Audit sufficiency rules. |
| `runtime/human-authorization-gates.md` | Human authorization gates. |
| `runtime/critical-decision-gates.md` | Critical decision gates. |
| `runtime/release-candidate-review.md` | Release candidate review. |
| `logs/CERTIFICATION_LOG.md` | Certification log. |
| `logs/GOVERNANCE_GATE_LOG.md` | Governance gate log. |
| `logs/RELEASE_CANDIDATE_REVIEW_LOG.md` | Release candidate review log. |

## Operating limits

Block 8 is documentary only.

It does not create:

- Business agents.
- Commercial, clinical, documentation, marketing, sales or operations agents.
- Databases, services, workers or external integrations.
- Permission changes.
- Secret management.
- Dependency installation.
- Destructive changes.
- Automatic merge.

## Acceptance criteria

- Certification Gates are defined.
- Governance Gate Matrix is defined.
- Pre-merge Governance Review is defined.
- Runtime Compliance Checklist is defined.
- Execution, Integration and Rollback Readiness Certification are defined.
- Evidence and Audit Sufficiency Rules are defined.
- Human Authorization and Critical Decision Gates are defined.
- Release Candidate Review is defined.
- Certification, governance and release candidate logs exist.
- Existing evidence, decision, audit, state and incident logs are updated.
- `git diff --check` passes.
- Pull request is opened against `main`.
- No merge is executed without explicit Tiziano authorization for that PR.

## v0.1.0 status

Status: documentary baseline.

Merge status: must remain unmerged until technical review and explicit Tiziano
authorization for the specific pull request.
