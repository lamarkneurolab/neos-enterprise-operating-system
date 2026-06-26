# Activation Request Log

This log records NEOS activation requests.

## Purpose

Track formal future activation requests after dry-run simulation review.

## Scope

Activation request metadata, scope, linked dry-run, evidence, audit, risk,
rollback, incident and decision status.

## Entry template

| Date | Request ID | Scope | Linked PR | Branch | Head SHA | Commit | Dry-Run Result | Evidence | Audit | Risk | Requested Action | Decision Status | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ISO 8601 date | Request identifier | Scope | PR | Branch | Head SHA | Commit | Dry-run reference | Evidence reference | Audit reference | Risk level | Requested action | Decision status | Notes |

## 2026-06-26 - Fase 3 Block 12

| Date | Request ID | Scope | Linked PR | Branch | Head SHA | Commit | Dry-Run Result | Evidence | Audit | Risk | Requested Action | Decision Status | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-26 | ACT-REQ-NEOS-F3-012 | Runtime Controlled Activation Gate & Execution Authorization Layer v0.1.0 | #10 | feature/runtime-controlled-activation-gate-execution-authorization-layer-v0.1.0 | 9b1d3211695c0833de885e79ca4b2939f5c641ed | 9b1d3211695c0833de885e79ca4b2939f5c641ed | SIM-NEOS-F3-012 | TEST-EVD-NEOS-F3-012 | AUD-NEOS-F3-012 | medium | documentation review only | review_required | Documentary activation request model recorded for Block 12 review only; no runtime activation or execution authorization granted. |
| 2026-06-26 | ACT-REQ-NEOS-F3-013 | Runtime Controlled Execution Activation Protocol v0.1.0 | pending PR | feature/runtime-controlled-execution-activation-protocol-v0.1.0 | pending head SHA | pending commit | ACT-SESSION-NEOS-F3-013 | PRE-ACT-EVD-NEOS-F3-013 | AUD-NEOS-F3-013 | medium | documentation review only | review_required | Documentary activation protocol model recorded for Block 13 review only; no runtime activation or execution authorization granted. |

## v0.1.0 status

Future entries must be traceable and auditable.
