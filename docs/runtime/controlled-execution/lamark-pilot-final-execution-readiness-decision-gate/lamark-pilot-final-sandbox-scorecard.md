# Lamark Pilot Final Sandbox Scorecard

## Purpose

This scorecard defines final sandbox readiness criteria for the Lamark pilot readiness decision gate.

## Scorecard

| Criterion | Required Condition | Gate Impact |
|---|---|---|
| Sandbox scope | Sandbox boundary is documented and current | Required |
| Allowed actions | Allowed actions remain documentary and non-production | Required |
| Excluded actions | Production, real integrations, and real agents remain blocked | Blocking |
| Sandbox evidence | Sandbox evidence package is referenced and reviewed | Required |
| Isolation | No dependency on live services, real customers, or real documents exists | Blocking |
| Sandbox handoff | Sandbox assumptions and open items are recorded | Required |

## Passing Rule

Sandbox readiness passes only when the pilot remains isolated, documentary, non-production, and free of real integrations or real agent creation.

## Failure Rule

Any production activation, real service dependency, real integration, real agent, real customer, or real document dependency fails this scorecard.

## Status

Version: v0.1.0
Scorecard status: documentary readiness only
Execution status: blocked
