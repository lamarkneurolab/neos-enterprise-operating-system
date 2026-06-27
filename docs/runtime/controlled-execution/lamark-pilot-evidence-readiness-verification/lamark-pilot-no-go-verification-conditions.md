# Lamark Pilot No-Go Verification Conditions

## Purpose

This document defines no-go verification conditions for Lamark pilot readiness.

## No-Go Conditions

Readiness verification must produce a no-go result if any of the following are true:

- Evidence is incomplete.
- Evidence cannot be traced to an approved source.
- Evidence cannot be correlated to audit.
- Human authorization is missing, expired, ambiguous, or out of scope.
- Sensitive financial data is present.
- Real customer data is present.
- Real documents were moved, deleted, shared, sent, transformed, or permission-modified without authorization.
- Runtime execution occurred or was attempted.
- Production activation occurred or was attempted.
- Agents, integrations, runners, CI, databases, or external services were created.
- Secrets were administered.
- Dependencies were installed.
- Files were deleted.
- Destructive changes occurred.
- Incident blockers are present or unresolved.
- Rollback readiness is incomplete.
- Handoff verification is incomplete.

## No-Go Rule

A no-go result keeps Lamark in documentary sandbox status and blocks any future operational action until a separately authorized remediation and review occurs.

## Status

Version: v0.1.0
Execution status: blocked
