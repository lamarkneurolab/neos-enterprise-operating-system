# Lamark Pilot Human Approval Record

## Purpose

This document defines the human approval record required by the Lamark pilot authorization gate.

## Required Approval Fields

Each approval record must include:

- Approver name or role.
- Approval date.
- Authorized scope.
- Prohibited scope acknowledged.
- Evidence package reference.
- Readiness verification reference.
- Authorized execution window reference.
- Expiration or review condition.
- Decision outcome.
- Explicit statement that approval applies only to the named action.

## Approval Limits

Human approval does not carry over from prior PRs, merges, blocks, or exhausted authorizations. Approval must be current, explicit, and scoped.

## Failure Rule

If approval is missing, expired, ambiguous, inherited, or broader than the documented boundary, authorization is denied.

## Status

Version: v0.1.0
Execution status: blocked
