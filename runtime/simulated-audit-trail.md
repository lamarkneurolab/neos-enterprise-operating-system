# Simulated Audit Trail

## Purpose

Define simulated audit records for dry-run review.

## Minimum fields

| Field | Requirement |
|---|---|
| `simulated_audit_id` | Stable simulated audit identifier. |
| `timestamp` | ISO 8601 timestamp. |
| `actor` | Reviewer or simulated actor. |
| `intention` | Intended simulated action. |
| `scope` | Simulated scope. |
| `risk` | Risk level. |
| `decision` | Review decision. |
| `result` | Simulated result. |
| `evidence_reference` | Simulated evidence reference. |

## Relationship with AUDIT_TRAIL

Simulated audit may reference `logs/AUDIT_TRAIL.md` for block-level
traceability, but it does not replace real audit required for future
activation.

## Rules

- Simulated audit must be clearly labeled.
- Simulated audit must not imply activation approval.
- Simulated audit must link evidence and result registry entries.

## Relationship with activation audit

Simulated audit may support activation audit requirements, but activation
authorization requires separate audit records for request, decision and scope.
