# Lamark Pilot Final Document Handling Scorecard

## Purpose

This scorecard defines final document handling readiness criteria for the Lamark pilot readiness decision gate.

## Scorecard

| Criterion | Required Condition | Gate Impact |
|---|---|---|
| Document class | Documents are test, synthetic, or documentary references only | Required |
| Real documents | No real customer documents are included or processed | Blocking |
| Copy controls | Any permitted copies are documentary and authorized | Required |
| Permission controls | No real permissions are changed | Blocking |
| Movement controls | No real documents are moved, deleted, shared, transformed, or transmitted | Blocking |
| Handling exceptions | Exceptions are documented with owner and decision disposition | Required |

## Passing Rule

Document handling readiness passes only when document use remains documentary and no real document operation is authorized or performed.

## Failure Rule

Any real document movement, deletion, sharing, transformation, permission change, external transmission, or unauthorized copy fails this scorecard.

## Status

Version: v0.1.0
Scorecard status: documentary readiness only
Execution status: blocked
