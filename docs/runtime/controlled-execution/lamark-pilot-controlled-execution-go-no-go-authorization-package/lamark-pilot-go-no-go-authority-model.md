# Lamark Pilot Go/No-Go Authority Model

## Purpose

This document defines the authority model for a future Lamark pilot Go/No-Go decision.

## Authority Requirements

- A named human decision owner must be recorded.
- The decision owner must have explicit authority for Go/No-Go determination.
- Delegated authority must be documented before use.
- Authority scope must distinguish readiness, authorization, and execution.
- Any future execution requires separate explicit human authorization.

## Authority Limits

The Go/No-Go authority model does not authorize runtime execution by itself.

No authority in this package may activate production, create real agents, create real integrations, modify permissions, manage secrets, install dependencies, start CI or runners, create databases, connect services, process real documents, involve real customers, or use sensitive financial data.

## Required Record Fields

- Decision owner.
- Role or governance function.
- Authorization scope.
- Decision date.
- Evidence reviewed.
- Conditions accepted or rejected.
- Explicit non-execution statement.

## Status

Version: v0.1.0
Authority status: documentary only
Execution status: blocked
