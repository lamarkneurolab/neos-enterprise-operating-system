# Closure Decision Protocol

## Purpose

Define the decision protocol for closing a future controlled execution after
post-monitoring review.

## Decision states

- closure_approved
- closure_rejected
- closure_deferred
- closure_invalidated
- incident_escalated
- rollback_required

## Closure rules

Closure may be approved only when result validation, final evidence, audit
closure, rollback review, incident linkage, unresolved risk review and human
closure approval are complete.

## Rejection rules

Closure must be rejected when scope was exceeded, evidence is insufficient,
audit is inconsistent, critical incident remains open, rollback is unresolved or
human approval is missing.

## Deferral rules

Closure may be deferred when evidence, audit, incident, rollback or risk review
requires additional documentary work.

## No automatic closure

Passing checks, successful monitoring or absence of visible incidents cannot
close execution automatically. Closure requires explicit human approval.
