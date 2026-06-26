# Decision Risk Review

## Purpose

This document defines risk review rules for Go / No-Go release decisions.

## Risk Categories

| Category | Meaning | Decision Effect |
|---|---|---|
| acceptable | Risk is documented, bounded, and accepted by the decision owner. | May support Go. |
| conditional | Risk requires remediation, evidence, or monitoring before reconsideration. | Conditional Hold. |
| blocking | Risk exceeds accepted limits or lacks controls. | No-Go. |
| invalid | Risk review is stale, mismatched, or unauditable. | Invalidated Decision. |

## Required Risk Inputs

- Risk acceptance certification.
- Release boundary.
- Runtime window.
- Monitoring boundary.
- Rollback readiness.
- Incident closure status.
- No-go conditions.
- Release gate invalidation rules.

## Review Rules

- Unaccepted high or critical risk blocks Go.
- New risk after decision invalidates prior Go.
- Risk tied to a changed head SHA or scope must be reviewed again.
- Risk accepted for one PR cannot be reused for another PR.

## Execution Boundary

Risk acceptance supports release decision governance only. It does not execute runtime or activate production.

## Status

Version: v0.1.0
Execution status: blocked
