# Activation Session Model

## Purpose

Define the bounded documentary container for one proposed future controlled
execution activation.

## Minimum fields

- activation_session_id
- authorization_reference
- PR
- branch
- head_sha
- commit
- scope
- action
- runtime_window
- approver
- timestamp
- evidence_references
- audit_reference
- rollback_reference
- incident_reference
- go_no_go_decision
- status

## Valid status values

- session-draft
- session-review-required
- session-ready-for-go-no-go
- session-held
- session-aborted
- session-closed

## Invalidity conditions

The session is invalid if PR, branch, head SHA, commit, scope, action, runtime
window, evidence, audit, rollback readiness or authorization changes without a
new review.

## Non-execution rule

An activation session records intent and controls only. It does not authorize or
start execution by itself.
