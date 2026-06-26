# Activation Denial & Deferral Rules

## Purpose

Define when activation requests are denied, deferred or blocked.

## Deny

Deny when requested action is prohibited, scope is invalid, authorization is
ambiguous or risk cannot be accepted.

## Defer

Defer when remediation is possible but evidence, audit, rollback, incident plan
or risk review is incomplete.

## Block

Block when PR, branch, head SHA, commit or scope changed after review, or when
prohibited execution is required.

## Missing evidence

Missing dry-run result, simulation evidence, audit, rollback, incident or risk
records prevents approval.

## Unresolved risk

High, critical and blocked risk cannot proceed without explicit escalation and
decision.

## Return to Block 11

Return to dry-run simulation when scope, risk, PR, branch, head SHA, commit or
requested action changes.

## Return from Block 13

Block 13 must return to denial, deferral or block review when activation
preconditions fail, scope changes, runtime window expires or go/no-go is not
explicit.
