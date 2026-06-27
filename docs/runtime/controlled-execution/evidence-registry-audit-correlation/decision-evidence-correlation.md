# Decision Evidence Correlation

## Purpose

This document defines how evidence is correlated with Go / No-Go and release decision records.

## Decision States

| Decision State | Evidence Interpretation | Execution Effect |
|---|---|---|
| Go | Historical or current decision evidence within its explicit scope and validity | None without separate execution authorization |
| No-Go | Blocking decision evidence | Blocks execution until superseded by a valid new decision |
| Conditional Go | Evidence of limited approval conditions | None outside explicit conditions |
| Conditional Hold | Evidence that required conditions remain unresolved | Blocks execution |
| Expired decision | Historical decision evidence | No current authorization |
| Invalidated decision | Superseded or rejected decision evidence | No current authorization |
| Superseded decision | Historical context for a later decision | No current authorization |

## Required Correlations

Decision evidence must link to decision identifier, related block, related PR, branch, base SHA, head SHA, check evidence, audit event, authorization reference, expiration status, invalidation status, and blocked execution status when applicable.

## Decision Rules

- Historical Go is not current Go.
- A No-Go blocks execution until superseded by a valid new decision.
- Conditional Go does not authorize work outside its explicit scope.
- Decision evidence does not execute runtime.

## Status

Version: v0.1.0
Execution status: blocked
