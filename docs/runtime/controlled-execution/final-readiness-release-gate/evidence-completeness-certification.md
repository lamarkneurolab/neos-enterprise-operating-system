# Evidence Completeness Certification

## Purpose

Certify that release gate evidence is complete and traceable.

## Scope

Evidence completeness covers authorization, activation, monitoring,
post-monitoring closure, audit, rollback, incidents, risks, human approvals and
release boundary evidence.

## Required inputs

- Release evidence package.
- Closure evidence sufficiency records.
- Monitoring evidence package.
- Audit records.
- Incident records.
- Rollback records.
- Human approval records.

## Expected outputs

- evidence_completeness_status
- missing_evidence
- evidence_blockers
- release_evidence_reference

## Control rules

Evidence completeness cannot be inferred from passing checks alone.

## Evidence minimum

Evidence must include PR, branch, head SHA, commit, scope, action, runtime
window, monitoring boundary, closure boundary and release boundary.

## Acceptance criteria

Evidence is complete only when it is current, scoped, auditable and sufficient
to support a human release decision.

## Invalidity conditions

Missing, stale, unaudited, contradictory or boundary-mismatched evidence
invalidates certification.

## Governance relationship

Evidence completeness must link audit, rollback, incident and human approval.

## Non-production rule

Evidence completeness does not release production or execute runtime.
