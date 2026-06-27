# Lamark Pilot Rollback Preconditions

## Purpose

This document defines rollback preconditions for the Lamark pilot authorization gate.

## Required Rollback Preconditions

Authorization requires:

- Rollback triggers documented.
- Stop conditions documented.
- Rollback owner documented.
- Incident escalation owner documented.
- Evidence rollback record defined.
- Handoff linkage documented.
- Human review requirement documented.

## Rollback Boundary

Rollback readiness is documentary preparedness only. It does not execute rollback procedures, modify production, or authorize operational changes.

## Failure Rule

If rollback triggers, ownership, stop conditions, or evidence requirements are missing, authorization is denied.

## Status

Version: v0.1.0
Execution status: blocked
