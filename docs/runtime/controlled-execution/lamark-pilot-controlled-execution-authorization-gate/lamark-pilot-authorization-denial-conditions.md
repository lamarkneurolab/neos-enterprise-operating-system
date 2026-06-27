# Lamark Pilot Authorization Denial Conditions

## Purpose

This document defines authorization denial conditions for the Lamark pilot authorization gate.

## Denial Conditions

Authorization must be denied if:

- Human approval is missing, expired, ambiguous, inherited, or out of scope.
- Evidence preconditions are incomplete.
- Sandbox readiness preconditions are incomplete.
- Data boundary preconditions fail.
- Document handling preconditions fail.
- Incident blockers are present or unresolved.
- Rollback preconditions are incomplete.
- Audit correlation preconditions fail.
- Handoff preconditions are incomplete.
- Runtime execution occurred or is requested by this gate.
- Production activation occurred or is requested by this gate.
- Agents, integrations, runners, CI, databases, or services are created.
- Permissions are modified.
- Secrets are administered.
- Dependencies are installed.
- Files are deleted.
- Real documents are touched without authorization.

## Denial Outcome

When authorization is denied, execution remains blocked and a future separately authorized remediation is required.

## Status

Version: v0.1.0
Execution status: blocked
