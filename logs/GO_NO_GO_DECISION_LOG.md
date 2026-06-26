# Go/No-Go Decision Log

This log records NEOS final go/no-go decision reviews.

## Purpose

Track explicit human go/no-go decisions for future controlled activation
sessions.

## Scope

Decision metadata, activation session, authorizer, exact PR, branch, head SHA,
commit, scope, action, runtime window, evidence, audit and decision outcome.

## Entry template

| Date | Decision ID | Activation Session ID | Authorizer | PR | Branch | Head SHA | Commit | Scope | Action | Runtime Window | Decision | Evidence | Audit | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ISO 8601 date | Decision ID | Session ID | Authorizer | PR | Branch | Head SHA | Commit | Scope | Action | Runtime window | `go`, `no-go`, `hold`, `abort` or `needs-review` | Evidence reference | Audit reference | Notes |

## 2026-06-26 - Fase 3 Block 13

| Date | Decision ID | Activation Session ID | Authorizer | PR | Branch | Head SHA | Commit | Scope | Action | Runtime Window | Decision | Evidence | Audit | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-26 | GO-NOGO-NEOS-F3-013 | ACT-SESSION-NEOS-F3-013 | Tiziano | #11 | feature/runtime-controlled-execution-activation-protocol-v0.1.0 | 547aa5145e7a832b6bb551b57c6df4f08c3364cd | 547aa5145e7a832b6bb551b57c6df4f08c3364cd | Runtime Controlled Execution Activation Protocol v0.1.0 | documentation review only | EXEC-WIN-NEOS-F3-013 | needs-review | PRE-ACT-EVD-NEOS-F3-013 | AUD-NEOS-F3-013 | No runtime go decision granted; merge and execution remain blocked pending explicit authorization for a specific PR and head SHA. |

## v0.1.0 status

Future entries must be traceable and auditable.
