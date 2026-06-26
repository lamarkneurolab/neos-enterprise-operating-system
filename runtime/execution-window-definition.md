# Execution Window Definition

## Purpose

Define how a future runtime execution window is documented before any controlled
activation can be considered.

## Minimum fields

- window_id
- activation_session_id
- proposed_start
- proposed_end
- timezone
- permitted_action
- permitted_scope
- operator_or_reviewer
- hold_conditions
- abort_conditions
- monitoring_preconditions
- evidence_reference
- audit_reference

## Window rule

An execution window is a condition for review, not authorization. A defined
window does not grant permission to execute.

## Blocking conditions

The window blocks activation review when timing is missing, scope is ambiguous,
the action exceeds authorization, monitoring prerequisites are absent or human
final approval has not been recorded.
