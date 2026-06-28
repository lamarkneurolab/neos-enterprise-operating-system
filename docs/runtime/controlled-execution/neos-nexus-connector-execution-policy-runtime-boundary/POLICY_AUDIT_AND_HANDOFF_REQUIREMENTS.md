# Policy Audit and Handoff Requirements

## Audit record

Each connector decision requires a compact audit record with the action request, connector class, tool name, target, mode, data class, risk tier, decision, reason, authorization reference, evidence reference, operator, timestamp, and safe-stop status.

## Handoff package

A handoff package is required whenever a decision is escalated, blocked, partially completed, or prepared for later execution. The package must be sufficient for a human reviewer to understand what was requested, what was allowed, what was not done, and what exact authorization would be required next.

## Minimum handoff fields

| Field | Requirement |
| --- | --- |
| Scope | Repository, branch, file, account, connector, environment, or target object. |
| Action | Read, draft, write, submit, activate, merge, delete, notify, or schedule. |
| Boundary | Data class, risk tier, production status, and external effect status. |
| Decision | Execute, prepare, escalate, or block. |
| Evidence | Links or references to local documents, authorization records, checklists, and validation output. |
| Next authority | Exact human approval needed, including PR number and Head SHA for merge decisions. |

## Evidence integrity

Evidence must be factual and limited. It must not include secrets, credentials, private customer data, C4-C7 data, or unnecessary copies of connector payloads. When sensitive material is encountered, record the classification and stop condition instead of reproducing the content.

## Batch handoff

For batch work, each block keeps its own audit record, branch, commit, PR, and merge authorization path. A batch summary may correlate the items, but it does not combine their approvals or allow shared merge authority.
