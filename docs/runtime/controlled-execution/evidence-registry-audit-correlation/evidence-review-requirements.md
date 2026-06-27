# Evidence Review Requirements

## Purpose

This document defines the minimum human review requirements for evidence registry and audit correlation records.

## Minimum Review Requirements

Each evidence package must include:

- Canonical source reference.
- Evidence type classification.
- Related block reference.
- Related PR, branch, base SHA, head SHA, and merge commit SHA when applicable.
- Check status evidence when applicable.
- Decision evidence when applicable.
- Authorization evidence when applicable.
- Audit event correlation when applicable.
- Expiration and invalidation review.
- Blocked execution review.

## Human Reviewer Role

A human reviewer must confirm that evidence is complete, current, canonical, non-conflicting, and correctly classified. Reviewer acceptance does not authorize runtime execution or production activation.

## Completeness Criteria

Evidence is complete only when required fields are populated or explicitly marked not applicable, source authority is known, related records are linked, and unresolved gaps are recorded.

## Conflict Checks

Review must identify conflicts between PR state, commit SHA, check status, authorization scope, decision state, expiration, invalidation, incident records, rollback records, handoff records, and blocked execution records.

## Staleness Checks

Historical evidence must be marked historical. Expired or invalidated evidence must be excluded from any active authorization interpretation.

## Canonical Source Checks

GitHub records are authoritative for Markdown documents, PR metadata, commits, SHAs, branches, merge commits, and checks. Mirrors or copies are supporting evidence only.

## Audit Correlation Checks

Audit correlation must verify traceability between evidence, actor, timestamp, related decision, related authorization, and related blocked execution status.

## Core Rules

- Evidence records do not authorize execution.
- Passing checks are validation evidence, not release authorization.
- Historical evidence is not current authorization.
- Audit correlation is traceability, not permission.
- Evidence correlaciona.
- Auditoria verifica.
- Nada ejecuta.

## Status

Version: v0.1.0
Execution status: blocked
