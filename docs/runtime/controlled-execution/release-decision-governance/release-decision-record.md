# Release Decision Record

## Purpose

This document defines the formal human Go / No-Go release decision record for Runtime Controlled Execution Release Decision Record & Go/No-Go Governance v0.1.0.

The record captures the decision context after final readiness certification and release gate review. It does not execute runtime, activate production, create agents, or authorize any future action by implication.

## Required Record Fields

| Field | Requirement |
|---|---|
| decision_record_id | Unique identifier for the Go / No-Go record. |
| PR | Exact pull request covered by the decision. |
| branch | Exact branch covered by the decision. |
| base_sha | Exact base SHA reviewed for the decision. |
| head_sha | Exact head SHA reviewed for the decision. |
| commit | Exact commit covered by the decision. |
| merge_commit | Merge commit if already applicable; otherwise not applicable. |
| scope | Exact controlled release scope reviewed. |
| runtime_window | Exact future runtime window, if one is proposed. |
| release_boundary | Explicit release boundary and excluded areas. |
| evidence_package | Link or reference to the release evidence package. |
| decision_owner | Human owner making the decision. |
| timestamp | Timestamp of decision recording. |
| decision | `go`, `no-go`, `conditional-hold`, or `invalidated-decision`. |
| final_status | Final governance status after review. |

## Decision Rules

- Readiness certification is not a release decision.
- Release gate review is not execution.
- A Go decision does not execute.
- A No-Go decision blocks execution.
- A release decision record does not activate production.
- Execution remains blocked until a future separately authorized execution action exists.

## Traceability Requirements

Every release decision record must link to final readiness certification, evidence completeness certification, audit integrity certification, risk acceptance certification, rollback readiness certification, incident closure certification, and the final readiness acceptance checklist from Block 16.

## Invalid Record Conditions

The record is invalid if the PR, branch, base SHA, head SHA, commit, scope, runtime window, release boundary, evidence package, decision owner, or decision text is missing, ambiguous, inherited from a prior authorization, or changed after approval.

## Status

Version: v0.1.0
Scope: Documentary governance only
Execution status: blocked
