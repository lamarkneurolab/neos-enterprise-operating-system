# Activation Request Model

## Purpose

Define minimum fields for a controlled activation request.

## Minimum fields

| Field | Requirement |
|---|---|
| `request_id` | Stable activation request identifier. |
| `request_date` | ISO 8601 date. |
| `requester` | Requesting person or governance role. |
| `scope` | Exact requested activation scope. |
| `target_block` | Target NEOS block or future execution area. |
| `target_runtime_area` | Runtime area affected. |
| `linked_pr` | PR linked to the request. |
| `linked_branch` | Branch linked to the request. |
| `linked_head_sha` | Exact head SHA linked to the request. |
| `linked_commit` | Exact commit linked to the request. |
| `linked_dry_run_result` | Dry-run result reference. |
| `linked_simulation_evidence` | Simulation evidence reference. |
| `linked_audit_entry` | Audit reference. |
| `linked_rollback_plan` | Rollback plan reference. |
| `linked_incident_plan` | Incident plan reference. |
| `risk_level` | `low`, `medium`, `high`, `critical` or `blocked`. |
| `requested_action` | Requested future action. |
| `authorization_required` | Human authorization requirement. |
| `decision_status` | Current decision status. |

## Rule

An activation request is not execution authorization.

## Block 13 linkage

An approved request can only move to Block 13 activation protocol review. It
does not execute and does not create an activation session automatically.
