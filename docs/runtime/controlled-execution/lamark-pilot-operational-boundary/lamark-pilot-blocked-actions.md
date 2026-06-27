# Lamark Pilot Blocked Actions

## Purpose

This document defines actions blocked during the controlled Lamark pilot.

## Blocked Actions

| Action | Block Reason | Required Resolution |
|---|---|---|
| Open production activation | Lamark is not open production | Future separate production authorization |
| External sales activity | Pilot excludes external sales | Future separate commercial authorization |
| Real customer workflow | Pilot excludes real customers | Future separate customer authorization |
| Sensitive financial data access | Pilot excludes sensitive financial data | Future separate data authorization and safeguards |
| External commercial diagnosis | Pilot excludes external diagnosis | Future separate diagnostic authorization |
| Autonomous action | Human authorization is required | Explicit scoped human authorization |
| Moving real documents | Real document handling is restricted | Explicit scoped authorization |
| Deleting real documents | Destructive action is restricted | Explicit scoped authorization |
| Sharing real documents | Disclosure is restricted | Explicit scoped authorization |
| Sending information | External communication is restricted | Explicit scoped authorization |
| Modifying permissions | Permission changes are restricted | Explicit scoped authorization |
| Transforming real documents | Real document transformation is restricted | Explicit scoped authorization |
| Runtime execution | Runtime is not authorized | Future separate execution authorization |
| Agent creation | Agents are not authorized | Future separate agent authorization |
| External integration creation | Integrations are not authorized | Future separate integration authorization |
| Runner, CI, database, or service creation | Infrastructure expansion is not authorized | Future separate infrastructure authorization |

## Blocking Rule

Blocked actions remain blocked until superseded by a valid new decision and explicit human authorization. Historical authorization is not current authorization.

## Status

Version: v0.1.0
Execution status: blocked
