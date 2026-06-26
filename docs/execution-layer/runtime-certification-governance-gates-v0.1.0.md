# Runtime Certification & Governance Gates v0.1.0

This is the canonical specification for NEOS Fase 3 Block 8.

Block 8 defines the minimum documentary certification and governance layer for
runtime execution, integration, rollback, evidence, audit, memory, SDK
contracts, integration contracts, critical decisions and release candidate
review.

## Purpose

The purpose of Block 8 is to determine whether a runtime action or documentary
change can be considered valid, closable, promotable, integrable,
rollback-ready, audit-ready and human-authorized.

Block 8 does not execute runtime work. It applies governance gates to runtime
work before closure, promotion, merge or release candidate approval.

## Scope

Included:

- Certification Gates.
- Governance Gate Matrix.
- Pre-merge Governance Review.
- Runtime Compliance Checklist.
- Execution Readiness Certification.
- Integration Readiness Certification.
- Rollback Readiness Certification.
- Evidence Sufficiency Rules.
- Audit Sufficiency Rules.
- Human Authorization Gates.
- Critical Decision Gates.
- Release Candidate Review.
- Certification, governance and release candidate logs.

## Non-goals

Excluded:

- Business agents.
- Commercial, clinical, documentation, marketing, sales or operations agents.
- Production runtime automation.
- External connector execution.
- Databases, services, workers or queues.
- Permission changes.
- Secret management.
- Dependency installation.
- Destructive changes.
- Automatic merge.

## Architecture

```text
Authorization Flow
  -> Execution Flow
  -> Runtime Coordination Layer
  -> Observability / Audit / Memory / SDK / Integration Contracts
  -> Certification Gates
  -> Governance Gate Matrix
  -> Human Authorization Gates
  -> Release Candidate Review
  -> Close, block, rollback or promote
```

Certification gates sit after the relevant runtime facts are available and
before closure, promotion, merge or release candidate approval. They do not
replace Authorization Flow; they verify that authorization, evidence, audit,
rollback and compatibility remain sufficient.

## Certification gate model

Every certification gate must declare:

| Field | Requirement |
|---|---|
| Purpose | Why the gate exists. |
| Entry condition | When the gate must be evaluated. |
| Approval condition | What must be true to pass. |
| Blocking condition | What prevents closure, merge or promotion. |
| Minimum evidence | Evidence required in `logs/EVIDENCE_LOG.md`. |
| Minimum audit | Audit required in `logs/AUDIT_TRAIL.md`. |
| Risk | Known risk controlled by the gate. |
| Rollback | Required rollback or containment path. |
| Reviewer | Responsible review role or human decision owner. |
| Timing | When the gate applies. |
| Logs | Logs that must be updated. |

The canonical gate catalog is `runtime/certification-gates.md`.

## Governance gate matrix

The governance matrix in `runtime/governance-gate-matrix.md` maps change type
and risk level to required gates, evidence, audit, authorization, rollback,
logs and allowed outcome.

The matrix is mandatory for runtime documentation, SDK contracts, integration
contracts, internal interfaces, extension rules, external boundaries, memory,
observability, task queue, event bus, state manager, release candidates,
rollback, incidents and compatibility.

## Pre-merge governance review

Every Fase 3 pull request must pass `runtime/pre-merge-governance-review.md`
before merge can be considered.

Pre-merge review must verify:

- Alignment with Blocks 1-7.
- No business agents or prohibited agent classes.
- No destructive changes.
- No permission changes.
- No secrets.
- No unauthorized dependencies.
- Markdown validity.
- Traceability to logs.
- Evidence sufficiency.
- Audit sufficiency.
- Rollback readiness.
- Compatibility impact.
- Critical decisions.
- Human authorization requirements.

Merge remains blocked until Tiziano explicitly authorizes that specific pull
request. Authorization for PR #5 does not apply to future PRs.

## Readiness certification

Block 8 defines three readiness certifications:

| Certification | File | Required before |
|---|---|---|
| Execution Readiness | `runtime/execution-readiness-certification.md` | Runtime execution flow can be considered ready. |
| Integration Readiness | `runtime/integration-readiness-certification.md` | Integration contract or boundary can be considered ready. |
| Rollback Readiness | `runtime/rollback-readiness-certification.md` | Change can be considered reversible or containable. |

Failure of a readiness certification blocks closure and requires either
remediation, documented incident handling or rollback.

## Evidence and audit sufficiency

Evidence sufficiency is defined in `runtime/evidence-sufficiency-rules.md`.
Audit sufficiency is defined in `runtime/audit-sufficiency-rules.md`.

Evidence must be verifiable, specific, current and linked to the governed
action. Audit must connect action, decision, evidence, authorization, incident
and rollback context when applicable.

Fabricated, ambiguous, stale or unsupported evidence is insufficient and blocks
closure or merge when evidence is required.

## Human authorization

Human authorization gates are defined in
`runtime/human-authorization-gates.md`.

Human authorization is mandatory for:

- Merge of any pull request.
- Dependency installation.
- Permission changes.
- Secret management.
- File deletion.
- Destructive changes.
- Activation of real external integrations.
- Creation of business agents or prohibited agent classes.
- Critical scope changes.
- Release candidate approval.
- Critical rollback execution.

## Release candidate review

Release candidate review is defined in
`runtime/release-candidate-review.md`.

No block can be declared a release candidate unless scope, files, validation,
traceability, logs, evidence, audit, rollback, restrictions, residual risks,
ChatGPT recommendation and Tiziano decision are documented.

## Rollback

Repository documentary rollback:

```text
git revert <block_8_commit_sha>
```

Pull request rollback before merge:

```text
Close the Block 8 pull request without merge.
```

Gate-level rollback:

1. Mark the failed certification as blocked.
2. Record the failure in `logs/CERTIFICATION_LOG.md`.
3. Record governance disposition in `logs/GOVERNANCE_GATE_LOG.md`.
4. Record incident if missing evidence, audit, authorization, compatibility or
   rollback affects closure.
5. Restore prior compatible documentation or close the PR without merge.

## Risk matrix

| Risk | Scenario | Impact | Control | Rollback |
|---|---|---|---|---|
| Missing evidence | Work closes without verifiable proof. | Unreliable runtime governance. | Evidence Sufficiency Rules. | Block closure and record incident. |
| Missing audit | Decision has no governance trace. | Review trail incomplete. | Audit Sufficiency Rules. | Block merge and remediate audit. |
| Missing authorization | PR, destructive action or external action proceeds without Tiziano approval. | Unauthorized governance change. | Human Authorization Gates. | Stop action; close PR or revert if needed. |
| Certification bypass | Runtime work skips readiness gate. | Unsafe promotion or closure. | Certification Gate Log. | Mark certification failed and block closure. |
| Contract contradiction | Block 8 weakens Block 7 contracts. | Integration ambiguity. | Compatibility Matrix and pre-merge review. | Restore previous compatible language. |
| External execution enabled | Real connector or side effect is activated. | Unauthorized external change. | External boundary and human authorization gates. | Stop, record incident and rollback only with approval. |
| Rollback not ready | Failure has no containment path. | Extended incident or unrecoverable state. | Rollback Readiness Certification. | Block promotion until rollback is defined. |

## Review checklist

- [ ] All source content is Markdown.
- [ ] No dependencies are added.
- [ ] No permissions are changed.
- [ ] No secrets are managed.
- [ ] No files are deleted.
- [ ] No destructive changes are executed.
- [ ] No business agents are created.
- [ ] No external integrations are activated.
- [ ] Certification gates include required fields.
- [ ] Governance matrix covers minimum change types.
- [ ] Pre-merge review blocks merge without explicit Tiziano authorization.
- [ ] Evidence and audit sufficiency rules are linked.
- [ ] Readiness certifications are documented.
- [ ] Release candidate review is documented.
- [ ] Logs are updated.
- [ ] `git diff --check` passes.
- [ ] Pull request is open against `main`.
- [ ] No merge has been executed.

## v0.1.0 status

Status: documentary baseline for review.

Canonical source: GitHub.

Official source format: Markdown.
