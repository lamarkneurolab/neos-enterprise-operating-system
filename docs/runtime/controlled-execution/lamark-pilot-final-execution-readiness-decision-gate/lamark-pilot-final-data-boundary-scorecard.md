# Lamark Pilot Final Data Boundary Scorecard

## Purpose

This scorecard defines final data boundary readiness criteria for the Lamark pilot readiness decision gate.

## Scorecard

| Criterion | Required Condition | Gate Impact |
|---|---|---|
| Allowed data | Allowed data classes are documented | Required |
| Blocked data | Sensitive financial data and real customer data are excluded | Blocking |
| Data minimization | Only required synthetic, dummy, or approved test data is referenced | Required |
| Data provenance | Data source and authorization are documented | Required |
| External transmission | No data transmission to external services is authorized | Blocking |
| Data exceptions | Exceptions are recorded with no-go or defer disposition | Required |

## Passing Rule

Data boundary readiness passes only when allowed data is documentary, bounded, non-sensitive, and approved for readiness review.

## Failure Rule

Any sensitive financial data, real customer data, unauthorized source, external transmission, or unresolved data exception fails this scorecard.

## Status

Version: v0.1.0
Scorecard status: documentary readiness only
Execution status: blocked
