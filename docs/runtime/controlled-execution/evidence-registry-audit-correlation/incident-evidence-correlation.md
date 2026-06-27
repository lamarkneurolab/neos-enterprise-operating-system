# Incident Evidence Correlation

## Purpose

This document defines how incident records are correlated with evidence and audit traceability.

## Required Fields

| Field | Description |
|---|---|
| incident_id | Stable incident identifier |
| incident_type | Documentation, governance, authorization, audit, runtime, data, security, or operational category |
| severity | Informational, low, medium, high, critical, or blocked |
| detected_by | Person, check, review, or audit event that detected the incident |
| related_runtime_stage | Related controlled execution stage |
| related_block | Related Block 13, 14, 15, 16, 17, 18, or 19 |
| related_evidence | Evidence records linked to the incident |
| required_review | Required human review before closure |
| closure_evidence | Evidence required to close the incident |

## Incident Rules

- Incident evidence documents risk and response context.
- Incident evidence does not authorize remediation execution by implication.
- Closure evidence does not activate production.
- Unresolved incident evidence may block execution review.

## Lamark Pilot Boundary

Lamark pilot incidents must remain inside controlled pilot review unless separately authorized. They must not trigger external customer actions, sensitive financial data processing, or autonomous document operations.

## Status

Version: v0.1.0
Execution status: blocked
