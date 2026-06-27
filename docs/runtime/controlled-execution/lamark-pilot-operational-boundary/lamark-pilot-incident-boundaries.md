# Lamark Pilot Incident Boundaries

## Purpose

This document defines incident boundaries for the Lamark controlled pilot.

## Blocking Incidents

| Incident | Execution Impact |
|---|---|
| Unauthorized real document access | Blocks readiness review |
| Sensitive financial data exposure | Blocks readiness review |
| Real customer data exposure | Blocks readiness review |
| External commercial diagnosis attempt | Blocks readiness review |
| Unauthorized document movement | Blocks readiness review |
| Unauthorized document deletion | Blocks readiness review |
| Unauthorized document sharing | Blocks readiness review |
| Unauthorized information sending | Blocks readiness review |
| Unauthorized permission modification | Blocks readiness review |
| Unauthorized document transformation | Blocks readiness review |
| Runtime execution attempt | Blocks readiness review |
| Production activation attempt | Blocks readiness review |
| Agent, integration, runner, CI, database, or service creation attempt | Blocks readiness review |

## Incident Evidence

Each incident must record incident identifier, type, severity, detector, affected boundary, related evidence, related audit event, required human review, closure condition, and blocked status.

## Closure Rule

Incident closure requires evidence and audit review. Closure does not authorize execution or production activation.

## Status

Version: v0.1.0
Execution status: blocked
