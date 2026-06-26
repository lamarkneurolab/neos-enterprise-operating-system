# Runtime Controlled Activation Gate & Execution Authorization Layer v0.1.0

This is the canonical specification for NEOS Fase 3 Block 12.

## Objective

Define the documentary gate and authorization layer that governs how a passed
simulation can become a formal future activation request under controlled
conditions.

## Scope

Included:

- Controlled Activation Gate.
- Execution Authorization Layer.
- Activation Request Model.
- Activation Decision Matrix.
- Activation Scope Definition.
- Risk Acceptance Rules.
- Human Approval Workflow.
- Pre-Execution Authorization Checklist.
- Activation Evidence Package.
- Activation Audit Requirements.
- Activation Denial & Deferral Rules.
- Emergency Stop / Abort Conditions.
- Post-Authorization Control Rules.

## Out of scope

Excluded:

- Productive orchestration.
- Business, commercial, clinical, documentation, marketing, sales or operations
  agents.
- Real external integrations.
- Runners, CI, services, workers, queues or databases.
- Permission changes, secret management or dependency installation.
- File deletion, destructive changes, automatic merge or real execution.

## Documentary architecture

```text
Block 11 Dry-Run / Simulation Result
  -> Activation Request Model
  -> Activation Evidence Package
  -> Activation Audit Requirements
  -> Risk Acceptance Rules
  -> Controlled Activation Gate
  -> Human Approval Workflow
  -> Execution Authorization Layer
  -> Post-Authorization Control Rules
  -> Emergency Stop / Abort Conditions
```

## Controlled Activation Gate

The gate evaluates whether the future execution request has exact scope,
validated dry-run result, sufficient evidence, sufficient audit, rollback
planning, incident mapping, risk acceptance and explicit human approval.

## Execution Authorization Layer

The authorization layer records approval, denial, deferral, blocking or abort
decisions. Authorization is invalid if PR, branch, head SHA, commit, scope or
requested action changes.

## Activation Request Model

Activation requests must include request metadata, scope, linked PR, branch,
head SHA, commit, dry-run result, evidence, audit, rollback, incident plan,
risk level, requested action and decision status.

## Activation Decision Matrix

Allowed decisions are `approve-for-future-execution`, `deny`, `defer`, `block`,
`abort`, `request-more-evidence`, `request-risk-review` and
`request-human-approval`.

## Activation Scope Definition

Scope must define functional limits, technical limits, affected runtime areas,
documentary dependencies and prohibited actions.

## Risk Acceptance Rules

Risk acceptance uses `low`, `medium`, `high`, `critical` and `blocked`.
High and critical risks require explicit human escalation. Blocked risk cannot
move forward.

## Human Approval Workflow

Tiziano is the human approving authority for controlled activation decisions
when user authorization is required. Approval, rejection, suspension and
escalation must be traceable.

## Pre-Execution Authorization Checklist

Checklist review confirms dry-run result, simulated evidence, simulated audit,
rollback plan, incident response mapping, exact scope, PR, branch, head SHA,
human authorization and abort conditions.

## Activation Evidence Package

The evidence package links Block 11 simulation logs, `logs/AUDIT_TRAIL.md`,
`logs/EVIDENCE_LOG.md`, `logs/DECISION_LOG.md`, rollback and incident plans.

## Activation Audit Requirements

Audit must record authorization, denial, deferral, post-authorization control
and invalidation events.

## Activation Denial & Deferral Rules

Activation is denied, deferred or blocked when evidence is missing, risk is
unresolved, scope changed, authorization is absent or simulation must be rerun.

## Emergency Stop / Abort Conditions

Abort conditions invalidate authorization before execution. Emergency stop
conditions govern future execution and require immediate human escalation.

## Post-Authorization Control Rules

After authorization, no unapproved scope, PR, branch, head SHA, commit, action,
permission, secret, dependency, integration or agent change may proceed without
new approval.

## Risks and controls

| Risk | Control |
|---|---|
| Dry-run pass is treated as execution approval | Activation request and execution authorization remain separate. |
| Authorization becomes reusable | Authorization is scoped to PR, branch, head SHA, commit, scope and action. |
| Gate is treated as executor | Gate and authorization layer are documentary and non-executing. |
| Missing evidence advances request | Evidence package is mandatory. |
| Risk acceptance is ambiguous | Risk acceptance log and escalation rules are required. |
| Emergency stop is undefined | Abort and emergency stop conditions are documented. |

## Acceptance criteria

- All Block 12 content is Markdown.
- No code, scripts, dependencies, runners, CI, databases or services are
  introduced.
- No productive orchestration, agents, external integrations, permissions or
  secrets are activated or changed.
- New activation and authorization logs exist.
- Block 11 documents reference Block 12 as the required next layer after
  dry-run/simulation.
- Existing validation, evidence, audit, decision and release readiness logs are
  updated.
- `git diff --check` passes.
- PR is opened against `main` and left unmerged.

## v0.1.0 status

Status: documentary baseline for review.

Canonical source: GitHub.

Official source format: Markdown.
