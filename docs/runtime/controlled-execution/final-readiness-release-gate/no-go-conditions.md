# No-Go Conditions

## Purpose

Define conditions that block a future release gate go decision.

## Scope

No-go conditions apply to final readiness, evidence, audit, risk, rollback,
incidents, closure and human approval.

## Required inputs

- Certification records.
- Release evidence package.
- Governance release gate review.
- Human release approval status.

## Expected outputs

- no_go_status
- no_go_reason
- required_remediation
- reviewer

## Control rules

Any active no-go condition blocks release gate go recommendation.

## Evidence minimum

No-go evidence must identify the condition, affected scope, audit reference and
required remediation.

## Acceptance criteria

No-go can be cleared only through corrected evidence, audit linkage and human
review.

## Invalidity conditions

Missing explanation, missing audit or unreviewed blocker invalidates no-go
resolution.

## Governance relationship

No-go conditions are binding for governance release gate review.

## Non-production rule

No-go review does not execute remediation or release production.
