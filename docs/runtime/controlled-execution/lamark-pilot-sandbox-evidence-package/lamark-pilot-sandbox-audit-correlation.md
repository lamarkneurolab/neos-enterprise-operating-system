# Lamark Pilot Sandbox Audit Correlation

## Purpose

This document defines audit correlation for Lamark sandbox evidence.

## Correlation Requirement

Every evidence record must be linkable to an audit event, authorization reference, decision point, or review checkpoint.

## Required Correlation Fields

Each correlation entry must include:

- Evidence ID.
- Audit event ID.
- Related authorization reference.
- Related decision or checklist item.
- Reviewer.
- Review date.
- Current status.

## Audit Boundary

Audit correlation verifies traceability. It does not grant permission to execute runtime, activate production, use real customers, access sensitive data, or perform autonomous actions.

## Missing Correlation Rule

If evidence cannot be correlated to audit and authorization records, readiness remains blocked until the gap is resolved.

## Status

Version: v0.1.0
Execution status: blocked
