# Evidence Source Classification

## Purpose

This document classifies evidence sources by type, authority, and permitted use for Runtime Controlled Execution Evidence Registry & Audit Correlation v0.1.0.

## Source Types

| Source | Authority | Permitted Use |
|---|---|---|
| GitHub PR | Canonical evidence | Review scope, branch, files, checks, merge state, and historical PR context |
| GitHub commit | Canonical evidence | Prove change history and source lineage |
| GitHub merge commit | Canonical evidence | Prove merge event history after merge |
| GitHub check status | Canonical evidence | Validate review status and technical pass / fail evidence |
| Markdown document | Canonical evidence when stored in GitHub | Define documentary governance state |
| Audit trail | Supporting or canonical evidence by source | Verify traceability and review chronology |
| Authorization ledger | Canonical documentary evidence | Link human authorization records from Block 18 |
| Release decision record | Canonical documentary evidence | Link Go / No-Go and release decision state from Block 17 |
| Rollback reference | Supporting evidence | Link rollback readiness or rollback action documentation |
| Incident reference | Supporting evidence | Link incident context, severity, review, and closure |
| Handoff record | Supporting evidence | Link owner transition and acceptance context |
| Blocked execution record | Canonical documentary evidence | Preserve blocked action state and unresolved conditions |

## Evidence Classes

| Class | Definition | Execution Effect |
|---|---|---|
| Canonical evidence | Source record maintained in the official GitHub repository or official GitHub metadata | None |
| Supporting evidence | Context that helps review a canonical record | None |
| Historical evidence | Evidence for a past state, prior PR, prior decision, or prior authorization | None |
| Expired evidence | Evidence outside its validity condition or review window | None |
| Invalidated evidence | Evidence superseded or rejected by a later record | None |
| Non-authorizing evidence | Any evidence that proves context without granting permission | None |

## Classification Rules

- Evidence records do not authorize execution.
- Passing checks are validation evidence, not release authorization.
- Historical evidence is not current authorization.
- Audit correlation is traceability, not permission.
- Expired or invalidated evidence cannot be used as active authorization.
- Prior authorization is evidence, not permission for future actions.

## Lamark Pilot Classification

Lamark pilot evidence must be classified as controlled pilot evidence unless a future separately authorized action states otherwise. It must not be classified as open production evidence, customer operation evidence, sales evidence, or autonomous execution permission.

## Status

Version: v0.1.0
Execution status: blocked
