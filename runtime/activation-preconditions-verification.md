# Activation Preconditions Verification

## Purpose

Define the checks required before an activation session can proceed to final
go/no-go review.

## Required checks

- Block 12 authorization reference is present.
- PR, branch, head SHA and commit match the authorized scope.
- Scope and action have not expanded.
- Runtime window is defined and bounded.
- Evidence package is sufficient.
- Audit record is sufficient.
- Rollback readiness is documented.
- Incident response mapping is current.
- Risk acceptance is current.
- No governance or certification blocker is unresolved.
- No permissions, secrets, dependencies, agents, runners, CI, databases,
  services or integrations are introduced.

## Blocking failures

Any failed check places the session in hold or abort. Missing validation,
evidence, audit, rollback readiness or human approval blocks advancement.
