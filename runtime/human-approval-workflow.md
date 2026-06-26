# Human Approval Workflow

## Purpose

Define the human approval workflow for activation decisions.

## Workflow

1. Submit activation request.
2. Verify scope, PR, branch, head SHA, commit and requested action.
3. Review dry-run result.
4. Review evidence, audit, rollback and incident plans.
5. Review risk acceptance.
6. Decide approve, deny, defer, block, abort or request more review.
7. Record decision in logs.

## Authority

Tiziano is the user authorizing authority when explicit human approval is
required.

## Approval conditions

Approval requires exact scope, sufficient evidence, sufficient audit, rollback
coverage, incident mapping, risk acceptance and no unresolved blocker.

## Rejection, suspension and escalation

Reject or suspend when scope changed, evidence is insufficient, risk is
unaccepted or authorization is ambiguous. Escalate high and critical risk.

## Traceability

All decisions must link activation request, decision, authorization, audit and
evidence records.
