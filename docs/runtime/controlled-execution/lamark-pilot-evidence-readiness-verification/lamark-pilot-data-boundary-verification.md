# Lamark Pilot Data Boundary Verification

## Purpose

This document defines data boundary verification for Lamark pilot evidence readiness.

## Required Data Boundary Checks

The verifier must confirm that evidence uses only:

- Synthetic examples.
- Redacted examples.
- Approved metadata.
- Approved taxonomy labels.
- Approved evidence identifiers.
- Approved audit identifiers.
- Approved authorization references.

## Blocked Data Checks

The verifier must confirm that evidence excludes:

- Sensitive financial data.
- Real customer data.
- Credentials.
- Secrets.
- Tokens.
- Unredacted personal data.
- Production-only data.
- External commercial diagnosis data.
- Data requiring permission changes.

## Failure Rule

If blocked data is present or data sensitivity is unclear, readiness verification fails until human review resolves the boundary.

## Status

Version: v0.1.0
Execution status: blocked
