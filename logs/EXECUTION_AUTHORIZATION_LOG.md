# Execution Authorization Log

This log records NEOS execution authorization decisions.

## Purpose

Track explicit authorization, denial, deferral, block and abort decisions.

## Scope

Execution authorization for future controlled activation only.

## Entry template

| Date | Authorization ID | Request ID | Authorizer | Scope | PR | Branch | Head SHA | Commit | Action | Decision | Expiration/Limit | Audit | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ISO 8601 date | Authorization identifier | Request ID | Authorizer | Scope | PR | Branch | Head SHA | Commit | Action | Decision | Expiration or limit | Audit reference | Notes |

## 2026-06-26 - Fase 3 Block 12

| Date | Authorization ID | Request ID | Authorizer | Scope | PR | Branch | Head SHA | Commit | Action | Decision | Expiration/Limit | Audit | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-26 | EXEC-AUTH-NEOS-F3-012 | ACT-REQ-NEOS-F3-012 | Tiziano | Block 12 implementation only | #10 | feature/runtime-controlled-activation-gate-execution-authorization-layer-v0.1.0 | 9b1d3211695c0833de885e79ca4b2939f5c641ed | 9b1d3211695c0833de885e79ca4b2939f5c641ed | create branch, Markdown files, commit, push and PR | implementation_only | No merge or execution authorization | AUD-NEOS-F3-012 | Authorization does not permit merge or activation. |
| 2026-06-26 | EXEC-AUTH-NEOS-F3-013 | ACT-REQ-NEOS-F3-013 | Tiziano | Block 13 implementation only | pending PR | feature/runtime-controlled-execution-activation-protocol-v0.1.0 | pending head SHA | pending commit | create branch, Markdown files, commit, push and PR | implementation_only | No merge, activation or execution authorization | AUD-NEOS-F3-013 | Authorization does not permit merge, activation or execution. |

## v0.1.0 status

Future entries must be traceable and auditable.
