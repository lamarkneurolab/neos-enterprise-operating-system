# Lamark Pilot Human Authorization Verification

## Purpose

This document defines human authorization verification for Lamark pilot readiness.

## Verification Requirements

Human authorization is verified only when the record includes:

- Approver.
- Approval date.
- Authorized action.
- Authorized scope.
- Evidence reference.
- Expiration or review condition.
- Statement that authorization applies only to the named action.

## Required Checks

The verifier must confirm that:

- Authorization exists.
- Authorization is current.
- Authorization matches the evidence scope.
- Authorization does not imply production activation.
- Authorization does not carry over from exhausted PR or merge approvals.
- Authorization does not permit autonomous action.

## Failure Rule

If authorization is missing, expired, ambiguous, inherited from a prior exhausted approval, or out of scope, readiness verification fails.

## Status

Version: v0.1.0
Execution status: blocked
