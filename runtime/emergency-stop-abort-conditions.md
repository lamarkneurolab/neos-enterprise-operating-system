# Emergency Stop / Abort Conditions

## Purpose

Define abort and emergency stop conditions for controlled activation review.

## Abort before execution

Abort before execution when authorization is missing, scope changed, evidence
is invalid, audit is missing, rollback is incomplete or incident risk is open.

## Emergency stop during future execution

Emergency stop applies to future execution only and must be triggered when
execution exceeds authorized scope, attempts prohibited actions or creates
unexpected high/critical risk.

## Immediate blocking

Immediate block is required for permission changes, secret handling,
dependency installation, external activation, agent creation or destructive
actions outside explicit authorization.

## Authorization invalidity

Authorization is invalid when PR, branch, head SHA, commit, scope, action,
evidence or risk changes.

## Log requirement

Abort and emergency stop records belong in
`logs/EMERGENCY_STOP_ABORT_LOG.md`.

## Human escalation

High, critical and scope-invalidating conditions require human escalation.
