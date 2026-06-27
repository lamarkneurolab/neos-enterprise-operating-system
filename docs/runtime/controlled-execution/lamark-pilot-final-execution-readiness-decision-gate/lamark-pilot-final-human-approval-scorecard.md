# Lamark Pilot Final Human Approval Scorecard

## Purpose

This scorecard defines final human approval readiness criteria for the Lamark pilot readiness decision gate.

## Scorecard

| Criterion | Required Condition | Gate Impact |
|---|---|---|
| Human decision owner | A named human owner is recorded | Required |
| Approval scope | Readiness approval scope is limited to documentary readiness | Required |
| Execution separation | Execution requires a separate explicit authorization | Blocking |
| Autonomous action | No autonomous action is authorized | Blocking |
| Approval evidence | Approval or no-go rationale is documented | Required |
| Delegation limits | Delegated authority is explicit and bounded if used | Required |

## Passing Rule

Human approval readiness passes only when the decision owner, scope, rationale, and execution separation are explicit.

## Failure Rule

Any implied approval, automated approval, ambiguous scope, or attempt to treat readiness as execution fails this scorecard.

## Status

Version: v0.1.0
Scorecard status: documentary readiness only
Execution status: blocked
