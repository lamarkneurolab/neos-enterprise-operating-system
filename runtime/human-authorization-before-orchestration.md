# Human Authorization Before Orchestration

## Purpose

Define when human authorization is required before future controlled
orchestration.

## When authorization is required

Human authorization is required when future orchestration involves:

- Merge approval.
- Critical or high-risk runtime decision.
- Productive execution.
- External integration activation.
- Permission, credential, secret or dependency impact.
- Rollback of critical scope.
- Incident escalation.
- Any ambiguous scope or governance/certification exception.

## Decisions requiring Tiziano

Tiziano authorization is required for:

- Merge of a relevant runtime PR.
- Critical execution approval.
- Approval of productive orchestration.
- Approval of exceptions to governance or certification blockers.
- Approval of any authorization that could affect canonical source, release
  posture or runtime execution authority.

## Non-reuse rule

Authorizations are not reusable.

Any merge or critical execution authorization applies only to the specific
case, PR number, branch, head SHA, scope, allowed action and expiration/scope
limit documented in that authorization.

## Minimum authorization fields

| Field | Requirement |
|---|---|
| `authorizer` | Human authorizer. |
| `scope` | Exact scope authorized. |
| `PR number` | Required when authorization applies to a PR. |
| `branch` | Source branch authorized. |
| `head SHA` | Exact head SHA authorized when applicable. |
| `allowed action` | Merge, controlled execution, rollback, exception or other action. |
| `expiration/scope limit` | Explicit expiration, one-time use or bounded scope. |

## Required rule

Every authorization for merge or critical execution applies only to the
specific case. Authorization from PR #7 does not apply to any future PR or
execution.

## Relationship with activation authorization

Future activation requires authorization under
`runtime/human-authorization-before-activation.md`. Authorization from PR #8
applied only to PR #8 and does not authorize Block 11 merge or any future
activation.
