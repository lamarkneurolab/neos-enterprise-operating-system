# Runtime Controlled Activation Gate & Execution Authorization Layer v0.1.0

This package establishes NEOS Fase 3 Block 12: Runtime Controlled Activation
Gate & Execution Authorization Layer v0.1.0.

Block 12 defines the documentary decision, authorization, evidence and control
framework for converting an approved simulation into a formal future activation
request. It does not activate productive orchestration and does not execute any
runtime action.

## Purpose

The purpose of Block 12 is to define the minimum controlled activation gate and
execution authorization layer required before any future real execution can be
considered.

## Relationship with Block 11

Block 11 defines dry-run, no-op and simulation review. Block 12 is the next
documentary layer: it evaluates whether a simulation result can become a formal
activation request.

Dry-run passed does not authorize execution.

Activation request does not authorize execution.

Authorization gate does not execute.

Execution authorization does not execute by itself.

## Controlled activation gate

The controlled activation gate evaluates scope, risk, evidence, audit,
rollback, incident posture, dry-run result and human authorization requirement
before a future execution request may proceed to review.

## Execution authorization layer

The execution authorization layer records the exact human authorization
required for future execution. Authorization is valid only for the approved
scope, PR, branch, head SHA, commit and action.

## Not permitted

Block 12 does not create or activate:

- Productive orchestration.
- Business, commercial, clinical, documentation, marketing, sales or operations
  agents.
- Real external integrations.
- Runners, CI, databases, services, workers or queues.
- Permission changes.
- Secret management.
- Dependency installation.
- File deletion or destructive changes.
- Automatic merge.
- Real execution.

## Critical rules

- Dry-run passed no autoriza ejecucion.
- Activation request no autoriza ejecucion.
- Authorization gate no ejecuta.
- Execution authorization no ejecuta por si sola.
- Only explicit human authorization can enable a future execution.
- Authorization applies only to the authorized scope, PR, branch, head SHA,
  commit and action.

## Included files

| File | Purpose |
|---|---|
| `docs/execution-layer/runtime-controlled-activation-gate-execution-authorization-layer-v0.1.0.md` | Canonical Block 12 specification. |
| `runtime/controlled-activation-gate.md` | Controlled activation gate model. |
| `runtime/execution-authorization-layer.md` | Execution authorization layer model. |
| `runtime/activation-request-model.md` | Activation request fields and requirements. |
| `runtime/activation-decision-matrix.md` | Activation decision matrix. |
| `runtime/activation-scope-definition.md` | Scope definition rules. |
| `runtime/risk-acceptance-rules.md` | Risk acceptance, denial and escalation rules. |
| `runtime/human-approval-workflow.md` | Human approval workflow. |
| `runtime/pre-execution-authorization-checklist.md` | Pre-execution authorization checklist. |
| `runtime/activation-evidence-package.md` | Activation evidence package. |
| `runtime/activation-audit-requirements.md` | Activation audit requirements. |
| `runtime/activation-denial-deferral-rules.md` | Denial and deferral rules. |
| `runtime/emergency-stop-abort-conditions.md` | Emergency stop and abort conditions. |
| `runtime/post-authorization-control-rules.md` | Post-authorization controls. |
| `logs/ACTIVATION_REQUEST_LOG.md` | Activation request log. |
| `logs/EXECUTION_AUTHORIZATION_LOG.md` | Execution authorization log. |
| `logs/RISK_ACCEPTANCE_LOG.md` | Risk acceptance log. |
| `logs/ACTIVATION_DECISION_LOG.md` | Activation decision log. |
| `logs/EMERGENCY_STOP_ABORT_LOG.md` | Emergency stop and abort log. |

## v0.1.0 status

Status: documentary baseline for review.

Canonical source: GitHub.

Official source format: Markdown.
