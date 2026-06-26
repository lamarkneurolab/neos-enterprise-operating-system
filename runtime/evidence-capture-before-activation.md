# Evidence Capture Before Activation

## Purpose

Define the evidence required before any future controlled runtime activation can
be considered.

## Minimum evidence

- Block 12 authorization reference.
- Activation session record.
- Scope lock record.
- Execution window record.
- Preconditions verification result.
- Go/no-go decision record.
- Rollback readiness record.
- Audit record reference.
- Incident response mapping.
- Validation output.

## Evidence rule

Evidence must be captured before activation, not after the start of future
execution. Missing evidence blocks go/no-go review.

## Log linkage

Pre-activation evidence belongs in `logs/PRE_ACTIVATION_EVIDENCE_LOG.md` and
may reference `logs/EVIDENCE_LOG.md`, `logs/AUDIT_TRAIL.md`,
`logs/DECISION_LOG.md` and Block 12 activation logs.
