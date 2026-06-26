# Incident Simulation Log

This log records NEOS incident simulation reviews.

## Purpose

Track simulated incidents for dry-run orchestration review.

## Scope

Simulated incident triggers, severity, escalation, response, evidence and
blocking status.

## Entry template

| Date | Simulated Incident ID | Scope | Trigger | Severity | Response | Evidence Reference | Audit Reference | Status | Reviewer | Notes |
|---|---|---|---|---|---|---|---|---|---|---|
| ISO 8601 date | Simulated incident identifier | Scope | Trigger | `low`, `medium`, `high` or `critical` | Response | Evidence reference | Audit reference | `open`, `contained`, `blocked`, `resolved` or `closed` | Reviewer | Notes |

## 2026-06-26 - Fase 3 Block 11

| Date | Simulated Incident ID | Scope | Trigger | Severity | Response | Evidence Reference | Audit Reference | Status | Reviewer | Notes |
|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-26 | SIM-INC-NEOS-F3-011 | Runtime Orchestration Dry-Run & Simulation Layer v0.1.0 | Activation attempted from simulation without authorization | medium | Block activation; require explicit future authorization | TEST-EVD-NEOS-F3-011 | AUD-NEOS-F3-011 | contained | Codex / NEOS Runtime Governance | Incident simulation model documented; no real incident or activation. |
| 2026-06-26 | SIM-INC-NEOS-F3-012 | Runtime Controlled Activation Gate & Execution Authorization Layer v0.1.0 | Execution attempted from activation request without authorization | high | Block execution; require explicit future authorization | TEST-EVD-NEOS-F3-012 | AUD-NEOS-F3-012 | contained | Codex / NEOS Runtime Governance | Emergency stop and abort model documented; no real incident or execution. |

## v0.1.0 status

Future entries must be traceable, auditable and clearly labeled as simulated.
