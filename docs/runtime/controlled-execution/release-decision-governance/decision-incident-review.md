# Decision Incident Review

## Purpose

This document defines incident review requirements before a Go / No-Go decision.

## Incident States

| State | Meaning | Decision Effect |
|---|---|---|
| closed-audited | Incident is closed and audit-linked. | May support Go. |
| open-low | Low incident remains open with accepted controls. | Human review required. |
| open-medium | Medium incident remains open with unresolved controls. | Conditional Hold or No-Go. |
| open-high | High incident remains open. | No-Go. |
| open-critical | Critical incident remains open. | No-Go. |
| unaudited | Incident lacks audit or evidence linkage. | No-Go or Invalidated Decision. |

## Required Review Inputs

- Incident closure certification.
- Incident record links.
- Evidence package links.
- Audit linkage.
- Rollback impact.
- Risk review impact.
- Human decision owner acknowledgement.

## Rules

- A critical open incident forces No-Go.
- An unaudited incident blocks Go.
- A new incident after Go invalidates the decision until reviewed.
- Incident acceptance cannot be inherited from a prior PR or scope.

## Execution Boundary

Incident review governs the release decision only. It does not execute incident response or activate production.

## Status

Version: v0.1.0
Execution status: blocked
