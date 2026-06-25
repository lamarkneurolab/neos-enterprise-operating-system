# ADR-0001 — Establish NEOS Source of Truth

## Status

Accepted

## Date

2026-06-25

## Context

NEOS is moving from conceptual architecture to executable Enterprise AI Platform infrastructure.

## Decision

The source-of-truth hierarchy is:

1. GitHub = canonical repository.
2. Markdown = official source format.
3. Google Drive = visual/documentary mirror.
4. Codex = engineering execution.
5. ChatGPT = architecture, orchestration and governance.

## Consequences

- Drive cannot override GitHub.
- Platform files must be maintained as Markdown first.
- Operational execution must produce auditable evidence.
