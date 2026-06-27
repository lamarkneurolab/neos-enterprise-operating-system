# Lamark Pilot Incident Blocker Preconditions

## Purpose

This document defines incident blocker preconditions for the Lamark pilot authorization gate.

## Required Preconditions

Authorization requires confirmation that incident blockers are absent or closed by human review.

## Blocking Incidents

Authorization is denied when any of the following are present:

- Unauthorized real document access.
- Unauthorized real document movement, deletion, sharing, sending, permission change, or transformation.
- Sensitive financial data exposure.
- Real customer data exposure.
- Credential, secret, token, or private key exposure.
- Runtime execution attempt.
- Production activation attempt.
- Autonomous action attempt.
- External commercial diagnosis attempt.
- External sales activity attempt.
- Missing evidence.
- Missing audit correlation.
- Missing human approval.

## Status

Version: v0.1.0
Execution status: blocked
