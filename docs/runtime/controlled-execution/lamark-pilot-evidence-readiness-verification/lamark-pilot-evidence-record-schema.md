# Lamark Pilot Evidence Record Schema

## Purpose

This document defines the minimum schema for each Lamark pilot evidence record.

## Minimum Evidence Record Fields

Each evidence record must include:

- Evidence ID.
- Evidence title.
- Evidence type.
- Source reference.
- Source owner.
- Sandbox scope linkage.
- Related readiness control.
- Related authorization reference.
- Audit event reference.
- Data boundary status.
- Document copy status.
- Sensitive data review status.
- Incident blocker status.
- Rollback readiness linkage.
- Handoff linkage.
- Reviewer.
- Review date.
- Current status.

## Required Status Values

Evidence records must use one of these statuses:

- Draft.
- Pending review.
- Accepted for documentary verification.
- Rejected.
- Blocked.
- Superseded.

## Boundary Rule

An accepted evidence record proves only that the record is suitable for documentary readiness verification. It does not authorize operational execution.

## Status

Version: v0.1.0
Execution status: blocked
