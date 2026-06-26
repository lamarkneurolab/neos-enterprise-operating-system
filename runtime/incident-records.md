# Incident Records Contract

The Incident Records contract defines the minimum record used to document
runtime failures, blocked conditions, degraded conditions and manual
intervention requirements.

The v0.1.0 Incident Records layer is documentary. It does not implement incident
automation, paging, monitoring integrations or remediation workers.

## Purpose

Incident Records preserve runtime conditions that require containment, review,
rollback or human intervention.

## Minimum incident types

| Incident type | Meaning |
|---|---|
| `unauthorized_execution_attempt` | Runtime attempted to execute without valid authorization. |
| `invalid_state_transition` | State Manager blocked an invalid transition. |
| `missing_evidence` | Required evidence was not available. |
| `missing_audit_entry` | Required audit entry was not available. |
| `event_dispatch_failure` | Event Bus could not record or dispatch an event contractually. |
| `rollback_failure` | Rollback could not complete or be evidenced. |
| `task_stuck` | Task did not reach an expected terminal or review state. |
| `runtime_component_unavailable` | Required runtime component was unavailable. |
| `manual_intervention_required` | Human action is required to contain or resolve the issue. |

## Minimum incident record

| Field | Requirement |
|---|---|
| `incident_id` | Required unique incident identifier. |
| `timestamp` | Required incident detection timestamp. |
| `severity` | Informational, warning, error or critical severity. |
| `affected_component` | Runtime component affected by the incident. |
| `task_id` | Linked task identifier when applicable. |
| `event_id` | Linked Event Bus event identifier when applicable. |
| `description` | Human-readable incident summary. |
| `detected_by` | Human, runtime component or review process that detected it. |
| `risk_level` | Low, medium, high or critical runtime risk. |
| `containment_action` | Immediate containment or stop condition. |
| `rollback_required` | `true`, `false` or `not_required`. |
| `rollback_ref` | Rollback reference when applicable. |
| `evidence_ref` | Evidence log reference. |
| `audit_ref` | Audit trail reference. |
| `status` | Current incident status. |

## Minimum statuses

| Status | Meaning |
|---|---|
| `open` | Incident is recorded and awaiting triage. |
| `triaged` | Incident has been reviewed and classified. |
| `contained` | Immediate containment action has been recorded. |
| `resolved` | Resolution has been recorded with evidence. |
| `rollback_required` | Rollback is required before closure. |
| `closed` | Incident is closed with evidence and audit references. |

## Rules

- Incidents must link evidence.
- Incidents with governance impact must link audit.
- Incidents requiring rollback must link rollback references.
- `unauthorized_execution_attempt` must block execution until authorization is
  resolved.
- `invalid_state_transition` must preserve the blocked transition and evidence.
- `missing_evidence` and `missing_audit_entry` must prevent closure until
  resolved or explicitly documented as manual remediation.

## Non-goals

- No incident management system is introduced.
- No alerting, paging or ticketing integration is introduced.
- No autonomous remediation is implemented.
