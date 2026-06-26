# Runtime Controlled Execution Activation Protocol v0.1.0

This is the canonical specification for NEOS Fase 3 Block 13.

## Objective

Define the documentary protocol that must be satisfied after a valid Block 12
authorization decision and before any future controlled runtime execution could
be considered.

## Scope

Included:

- Controlled Execution Activation Protocol.
- Activation Session Model.
- Execution Window Definition.
- Go/No-Go Decision Protocol.
- Activation Preconditions Verification.
- Runtime Activation Scope Lock.
- Human Final Approval Check.
- Execution Start Conditions.
- Execution Hold Conditions.
- Execution Abort Conditions.
- Evidence Capture Before Activation.
- Audit Record Before Activation.
- Rollback Readiness Before Activation.
- Post-Activation Monitoring Preconditions.
- Activation Handoff Rules.

## Out of scope

Excluded:

- Productive orchestration.
- Real runtime activation.
- Business, commercial, clinical, documentation, marketing, sales or operations
  agents.
- Real external integrations.
- Runners, CI, services, workers, queues or databases.
- Permission changes, secret management or dependency installation.
- File deletion, destructive changes, automatic merge or real execution.

## Documentary architecture

```text
Block 12 Execution Authorization Decision
  -> Controlled Execution Activation Protocol
  -> Activation Session Model
  -> Activation Preconditions Verification
  -> Runtime Activation Scope Lock
  -> Execution Window Definition
  -> Evidence Capture Before Activation
  -> Audit Record Before Activation
  -> Rollback Readiness Before Activation
  -> Human Final Approval Check
  -> Go/No-Go Decision Protocol
  -> Activation Handoff Rules
  -> Future controlled execution, still separately blocked
```

## Controlled Execution Activation Protocol

The protocol defines the ordered documentary checks required before a future
execution can be handed off for final human go/no-go. It does not invoke tools,
activate runtime, start orchestration or modify state.

## Activation Session Model

An activation session is the bounded documentary container for one proposed
future activation. It must identify the authorization reference, PR, branch,
head SHA, commit, scope, requested action, runtime window, approver, timestamp
and evidence references.

## Execution Window Definition

The execution window defines the proposed start boundary, end boundary,
timezone, allowed action and stop conditions. A window is necessary context, not
permission to execute.

## Go/No-Go Decision Protocol

The final decision must be explicit and human. Allowed outcomes are `go`,
`no-go`, `hold`, `abort` and `needs-review`. A `go` decision is valid only for
the exact session, scope, PR, branch, head SHA, commit, action and runtime
window.

## Activation Preconditions Verification

Preconditions verify that Block 12 authorization, scope, evidence, audit,
rollback, incident response and risk acceptance remain valid and unchanged.

## Runtime Activation Scope Lock

The scope lock prevents expansion of scope, PR, branch, head SHA, commit,
action, runtime area, permissions, secrets, dependencies, integrations, agents
or runtime window without a new authorization cycle.

## Human Final Approval Check

Tiziano is the human approving authority when explicit user authorization is
required. Final approval must name the exact PR, branch, head SHA, commit,
scope, action and runtime window.

## Execution Start Conditions

Start conditions are documentary prerequisites. They do not start execution.
Future execution remains blocked unless final human go/no-go is present and all
preconditions remain valid.

## Execution Hold Conditions

Hold conditions pause the future activation path when evidence, audit,
authorization, scope, runtime window, rollback readiness, incident response or
risk posture is incomplete or stale.

## Execution Abort Conditions

Abort conditions invalidate the activation session before execution. Scope
change, SHA change, missing approval, failed validation, insufficient evidence
or unresolved high/critical risk must abort the session.

## Evidence Capture Before Activation

Pre-activation evidence must capture the authorization reference, decision
reference, scope lock, runtime window, validation status, rollback readiness,
audit record and final go/no-go decision.

## Audit Record Before Activation

The audit record must preserve why the activation session was allowed to reach
go/no-go review, who approved it, what exact scope was reviewed and what was
blocked.

## Rollback Readiness Before Activation

Rollback readiness is a precondition. It must be documented before any future
start can be considered, not after execution begins.

## Post-Activation Monitoring Preconditions

Monitoring prerequisites define what future observation, evidence capture,
audit linkage and incident escalation must exist before any real activation.
They do not activate monitoring services or runtime execution.

## Activation Handoff Rules

Handoff transfers a fully documented activation session for final review. It is
not execution authorization by itself and cannot expand the approved scope.

## Risks and controls

| Risk | Control |
|---|---|
| Block 12 authorization is treated as execution | Block 13 repeats that authorization approved does not execute. |
| Protocol is treated as an executor | Every Block 13 document states it is documentary and non-executing. |
| Execution window becomes implicit permission | Window definition is recorded as necessary context only. |
| Scope expands after authorization | Scope lock invalidates changed PR, branch, SHA, commit, scope, action or window. |
| Final approval is missing | Go/no-go protocol requires explicit human decision. |
| Rollback is prepared too late | Rollback readiness is a pre-activation prerequisite. |
| Hold and abort are ambiguous | Start, hold and abort conditions are separated. |

## Acceptance criteria

- All Block 13 content is Markdown.
- No code, scripts, dependencies, runners, CI, databases or services are
  introduced.
- No productive orchestration, real activation, agents, external integrations,
  permissions or secrets are activated or changed.
- Activation session, go/no-go, execution window, scope lock and
  pre-activation evidence logs exist.
- Block 12 documents reference Block 13 as the required protocol after
  authorization and before any future execution.
- Existing validation, evidence, audit, decision and release readiness logs are
  updated.
- `git diff --check` passes.
- PR is opened against `main` and left unmerged.

## v0.1.0 status

Status: documentary baseline for review.

Canonical source: GitHub.

Official source format: Markdown.
