# Lamark Pilot Sandbox Sensitive Data Blocklist

## Purpose

This document defines sensitive data that must not enter the Lamark documentary sandbox.

## Blocklisted Data

The following data is blocked:

- Sensitive financial data.
- Banking data.
- Payment data.
- Tax data.
- Payroll data.
- Customer records.
- Real client files.
- Unredacted personal data.
- Credentials.
- Secrets.
- API keys.
- Access tokens.
- Private keys.
- Authentication artifacts.
- Health diagnosis data.
- Legal privilege data.
- Contract terms not approved for sandbox use.
- Any data whose handling requires production permissions.

## Handling Rule

Blocklisted data must not be copied, transformed, summarized, shared, sent, stored, classified, or included in evidence records for sandbox preparation.

## Exception Rule

Exceptions are not allowed inside this package. Any future exception requires separate human authorization and a separate evidence record before handling occurs.

## Status

Version: v0.1.0
Execution status: blocked
