# Release Evidence Package

## Purpose

Define the evidence package required for final release gate review.

## Scope

The package aggregates final readiness, closure, monitoring, evidence, audit,
risk, rollback, incident and human approval records.

## Required inputs

- Final readiness certification.
- Runtime closure certification.
- Evidence completeness certification.
- Audit integrity certification.
- Risk acceptance certification.
- Rollback readiness certification.
- Incident closure certification.
- Governance release gate review.
- Human release approval.

## Expected outputs

- release_evidence_package_id
- included_evidence
- missing_evidence
- evidence_sufficiency_status

## Control rules

Release evidence package is documentary and cannot execute or release.

## Evidence minimum

The package must include exact PR, branch, head SHA, commit, scope, action,
runtime window, monitoring boundary, closure boundary and release boundary.

## Acceptance criteria

The package is acceptable only when every certification can be traced to
evidence and audit.

## Invalidity conditions

Missing required evidence or audit references invalidate the package.

## Governance relationship

The package feeds governance release gate and human release approval.

## Non-production rule

Release evidence package does not liberate production.
