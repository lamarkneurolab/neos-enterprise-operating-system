# Risk Acceptance Rules

## Purpose

Define risk acceptance rules for activation requests.

## Risk levels

| Level | Meaning |
|---|---|
| `low` | Limited documentary risk. |
| `medium` | Controlled risk requiring evidence and audit. |
| `high` | Critical control risk requiring human escalation. |
| `critical` | Severe risk requiring explicit human decision and likely deferral. |
| `blocked` | Risk cannot be accepted in current scope. |

## Acceptance rules

Low and medium risk may proceed to human approval review when evidence, audit,
rollback and incident plans are complete.

## Denial rules

Requests are denied when risk is unsupported, scope is ambiguous, evidence is
missing, audit is missing or prohibited action is required.

## Escalation rules

High and critical risk require explicit human escalation and traceable risk
acceptance.

## Re-simulation rules

New simulation is required when scope, PR, branch, head SHA, commit, action,
risk level, rollback plan or incident plan changes.

## Additional rollback rules

Additional rollback review is required when risk increases or rollback
coverage is incomplete.
