# Rollback Playbooks

## Purpose

Define how rollback must be documented for future controlled orchestration.

## Rollback documentation requirements

A rollback playbook must include:

- Rollback scope.
- Preconditions.
- Trigger conditions.
- Ordered rollback steps.
- Evidence required.
- Audit required.
- Incident linkage when applicable.
- Completion criteria.
- Human escalation conditions.

## Preconditions

- Affected scope is known.
- Prior state or acceptable containment state is documented.
- Evidence and audit references are available.
- Human authorization requirement is resolved for critical rollback.

## Rollback triggers

- Failed validation.
- Failed verification.
- Missing evidence or audit during execution.
- Unauthorized state transition.
- Open high or critical incident.
- Governance or certification blocker discovered after approval.
- Productive execution attempt outside approved scope.

## Rollback evidence

Rollback evidence must show the rollback decision, affected scope, action
taken, result and reviewer.

## Rollback audit

Rollback decisions with governance or runtime impact must link to
`logs/AUDIT_TRAIL.md` and any incident record.

## Completion criteria

- Rollback or containment result is documented.
- Evidence is sufficient.
- Audit is sufficient.
- Incident status is updated when applicable.
- Readiness is re-reviewed before any future attempt.

## Relationship with rollback validation

Rollback playbooks must remain consistent with `runtime/rollback-validation.md`.
Rollback readiness must fail when a rollback path is missing, unreviewed or
not aligned with the affected runtime scope.

## Relationship with simulated rollback

Rollback playbooks must be rehearsed through
`runtime/simulated-rollback-flow.md` before any future activation request.
Simulated rollback does not execute real rollback and does not approve
activation.
