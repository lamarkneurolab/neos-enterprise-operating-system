# Risk Acceptance Certification

## Purpose

Certify that residual release risks are reviewed, accepted or blocked.

## Scope

Risk acceptance covers unresolved risks from activation, monitoring, closure,
rollback, incidents, evidence and audit review.

## Required inputs

- Unresolved risk register.
- Incident linkage review.
- Rollback readiness certification.
- Audit integrity certification.
- Human release approval.

## Expected outputs

- risk_acceptance_status
- residual_risk_list
- blocked_risks
- human_acceptance_reference

## Control rules

Residual risk cannot be accepted automatically and cannot exceed the release
boundary.

## Evidence minimum

Risk evidence must identify severity, owner, impact, affected scope, evidence,
audit, incident and rollback references.

## Acceptance criteria

Risk is acceptable only when residual risk is documented and human approval is
explicit where required.

## Invalidity conditions

Critical unaccepted risk, missing owner, missing evidence or absent human
approval invalidates certification.

## Governance relationship

Risk acceptance must link audit, rollback, incident and human approval records.

## Non-production rule

Risk acceptance does not authorize production release by itself.
