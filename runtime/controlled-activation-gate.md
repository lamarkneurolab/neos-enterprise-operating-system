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

## Primary gate states

| State | Meaning |
|---|---|
| `activation-requested` | A formal activation request exists. |
| `activation-review-required` | The request requires gate review before any future execution authorization. |
| `activation-approved-for-future-execution` | The request may proceed to separately scoped future execution authorization. |
| `activation-denied` | The request is denied. |
| `activation-deferred` | The request is postponed pending remediation or additional review. |
| `activation-blocked` | The request cannot proceed due to blocker. |
| `activation-aborted` | The request is stopped due to abort condition. |

## Auxiliary or derived states

| State | Meaning |
|---|---|
| `not_requested` | No activation request exists. |
| `evidence_required` | Evidence package is incomplete. |
| `risk_review_required` | Risk acceptance is unresolved. |
| `human_approval_required` | Explicit human approval is required. |

The primary gate states are the Block 12 contract. Auxiliary states may be used
only to explain why a primary state was reached.

## Blocks

The gate blocks activation when dry-run, evidence, audit, rollback, incident
mapping, scope, risk acceptance or human authorization is missing or changed.

## Evidence required

Activation evidence package, simulation result, audit reference, rollback
plan, incident plan and decision record.

## Automatic decision limits

The gate cannot automatically approve execution. It can only route the request
to explicit human authorization review.
