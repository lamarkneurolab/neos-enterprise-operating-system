# Operational Runbooks

## Purpose

Define operational runbooks allowed in documentary v0.1.0.

## Runbook versus playbook

A runbook documents a recurring operational review procedure. A playbook
documents a bounded future execution sequence.

Neither a runbook nor a playbook authorizes productive execution by itself.

## Standard runbook structure

| Field | Requirement |
|---|---|
| `runbook_id` | Stable runbook identifier. |
| `purpose` | Review purpose. |
| `scope` | Included and excluded areas. |
| `inputs` | Required logs, documents or evidence. |
| `review_steps` | Ordered review actions. |
| `decision_outputs` | Possible decisions and required records. |
| `evidence_required` | Evidence required for the review. |
| `audit_required` | Audit records required for governance-relevant decisions. |
| `escalation_conditions` | Conditions requiring human escalation. |

## Runbooks permitted in v0.1.0

- Readiness review.
- Validation review.
- Evidence review.
- Audit review.
- Rollback readiness review.
- Incident intake review.

## Prohibition

Block 10 runbooks must not execute real productive operations, activate
external systems, create agents, change permissions, manage secrets or install
dependencies.
