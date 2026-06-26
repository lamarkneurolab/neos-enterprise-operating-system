# Controlled Activation Gate

## Purpose

Define the documentary gate that evaluates future activation requests.

## Definition

The controlled activation gate is a review control that decides whether a
future execution request may proceed to authorization review.

## Evaluates

- Dry-run result.
- Activation request scope.
- Evidence package.
- Audit package.
- Rollback plan.
- Incident plan.
- Risk acceptance.
- Human approval requirement.

## Gate states

| State | Meaning |
|---|---|
| `not_requested` | No activation request exists. |
| `review_required` | Request exists and requires gate review. |
| `evidence_required` | Evidence package is incomplete. |
| `risk_review_required` | Risk acceptance is unresolved. |
| `human_approval_required` | Explicit human approval is required. |
| `approved_for_future_execution_review` | Request may proceed to future execution authorization review. |
| `denied` | Request is denied. |
| `deferred` | Request is postponed pending remediation. |
| `blocked` | Request cannot proceed. |
| `aborted` | Request is stopped due to abort condition. |

## Blocks

The gate blocks activation when dry-run, evidence, audit, rollback, incident
mapping, scope, risk acceptance or human authorization is missing or changed.

## Evidence required

Activation evidence package, simulation result, audit reference, rollback
plan, incident plan and decision record.

## Automatic decision limits

The gate cannot automatically approve execution. It can only route the request
to explicit human authorization review.
