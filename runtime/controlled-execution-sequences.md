# Controlled Execution Sequences

## Purpose

Define the documentary sequence model for future controlled runtime execution.

## Minimum order

1. Intake.
2. Scope confirmation.
3. Validation mapping.
4. Readiness check.
5. Authorization gate.
6. Execution window definition.
7. Evidence collection.
8. Audit logging.
9. Rollback readiness.
10. Completion review.

## Permitted states

| State | Meaning |
|---|---|
| `not_ready` | Required readiness material is missing. |
| `readiness_review_required` | Review is needed before eligibility. |
| `orchestration_eligible` | Criteria are sufficient for authorization review. |
| `human_authorization_required` | Specific human approval is required. |
| `orchestration_approved` | Specific controlled orchestration is approved. |

## Blocking states

| State | Blocking condition |
|---|---|
| `execution_blocked` | Missing validation, evidence, audit, rollback, authorization or gate approval. |
| `rollback_required` | Rollback or containment is required before closure. |
| `incident_response_required` | Incident response must be completed or escalated before continuation. |

## Sequence rule

Controlled execution must not start from eligibility alone. It may only proceed
after authorization and all applicable validations, evidence, audit and
rollback readiness are resolved for the specific scope.

## Relationship with dry-run simulation

Controlled execution sequences must be simulated in no-op mode before future
activation can be considered. A simulated sequence does not modify real state
and does not authorize activation.
