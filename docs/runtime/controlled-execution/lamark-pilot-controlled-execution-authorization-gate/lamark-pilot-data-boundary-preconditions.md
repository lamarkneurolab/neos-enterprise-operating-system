# Lamark Pilot Data Boundary Preconditions

## Purpose

This document defines data boundary preconditions for the Lamark pilot authorization gate.

## Allowed Data Preconditions

Authorization requires confirmation that only allowed documentary data is used:

- Synthetic examples.
- Redacted examples.
- Approved metadata.
- Approved taxonomy labels.
- Approved evidence identifiers.
- Approved audit identifiers.
- Approved authorization references.

## Blocked Data Preconditions

Authorization is denied if evidence or scope includes sensitive financial data, real customer data, credentials, secrets, tokens, unredacted personal data, production-only data, or data requiring permission changes.

## Boundary Rule

If sensitivity is unclear, the data is treated as blocked until human review confirms otherwise.

## Status

Version: v0.1.0
Execution status: blocked
