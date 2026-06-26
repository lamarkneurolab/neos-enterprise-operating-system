# Incident Response Playbooks

## Purpose

Define incident response playbooks for future controlled orchestration review.

## Operational incident types

- Missing authorization.
- Unauthorized execution attempt.
- Missing validation.
- Missing or invalid evidence.
- Missing or invalid audit trail.
- Failed verification.
- Invalid state transition.
- Rollback failure or missing rollback path.
- External integration boundary violation.
- Productive orchestration attempted outside approved scope.

## Activation conditions

Incident response activates when an execution, readiness review or validation
review detects a condition that may block continuation, require containment,
require rollback or require human escalation.

## Severity

| Severity | Meaning |
|---|---|
| `low` | Documentary inconsistency with limited scope. |
| `medium` | Missing control that blocks readiness until remediated. |
| `high` | Governance, certification, authorization, evidence, audit or rollback gap affecting critical scope. |
| `critical` | Unauthorized productive execution, severe boundary violation or unresolved high-risk incident. |

## Minimum incident fields

| Field | Requirement |
|---|---|
| `incident_id` | Stable incident identifier. |
| `date` | ISO 8601 date. |
| `severity` | `low`, `medium`, `high` or `critical`. |
| `trigger` | Condition that activated incident response. |
| `scope` | Affected runtime scope. |
| `evidence_reference` | Evidence supporting the incident. |
| `audit_reference` | Audit trail reference. |
| `rollback_reference` | Rollback reference when applicable. |
| `owner` | Reviewer or responder. |
| `status` | Open, contained, escalated, resolved or closed. |

## Log relationship

Runtime incidents must link to `logs/INCIDENT_LOG.md`. Playbook reviews must
link to `logs/INCIDENT_RESPONSE_PLAYBOOK_LOG.md`.

## Relationship with rollback

High and critical incidents must evaluate rollback or containment before
closure.

## Human escalation

Human escalation is required when severity is high or critical, authorization
is missing, productive execution is attempted, rollback is blocked or scope is
ambiguous.
