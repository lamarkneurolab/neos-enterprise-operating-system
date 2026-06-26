# Audit Playbooks

## Purpose

Define minimum audit requirements for future controlled orchestration.

## Minimum audit fields

| Field | Requirement |
|---|---|
| `audit_id` | Stable audit identifier. |
| `date` | ISO 8601 date. |
| `scope` | Runtime scope under review. |
| `actor` | Human or system actor. |
| `decision` | Decision or event audited. |
| `authorization_reference` | Human or governance authorization reference when applicable. |
| `evidence_reference` | Evidence supporting the decision or event. |
| `rollback_reference` | Rollback reference when applicable. |
| `incident_reference` | Incident reference when applicable. |
| `outcome` | Approved, blocked, rolled back, escalated or closed. |

## Relationship with audit trail

Governance-relevant orchestration decisions must link to
`logs/AUDIT_TRAIL.md`.

## Relationship with audit validation

Audit playbooks must remain consistent with `runtime/audit-validation.md`.
Missing, ambiguous, stale or scope-mismatched audit records block readiness and
closure.

## Traceability rules

- Audit must link to evidence.
- Authorization decisions must link to their exact scope.
- Rollback and incident decisions must preserve sequence and reviewer.
- Audit entries must not imply execution approval unless the approved action,
  scope and authorization are explicit.

## Relationship with simulated audit

Block 11 simulated audit supports dry-run review only. Simulated audit must not
replace real audit required for a future authorized activation.
