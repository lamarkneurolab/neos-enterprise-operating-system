# Human Approval Evidence Requirements

## Purpose

Human approval evidence must show what was authorized, by whom, for which object, and under which boundary.

## Required Evidence

| Field | Requirement |
| --- | --- |
| Authorizing party | Valid human authority for the action class. |
| Timestamp | Authorization time and validation time. |
| Scope | Exact connector, account, environment, object, file, PR, branch, Head SHA, or payload. |
| Action | Requested operation classified by risk. |
| Data class | Allowed data class and handling boundary. |
| Result path | Expected result and safe stop condition. |
| Reversibility | Rollback method or documented irreversibility. |

## Evidence Quality Rules

- Approval must be specific, current, and tied to the action.
- Batch approval cannot replace exact PR and Head SHA for merge.
- Draft approval cannot become send, submit, activate, or publish approval.
- Preparation approval cannot become live execution approval.
- Evidence must not include secret values or unnecessary restricted data.
