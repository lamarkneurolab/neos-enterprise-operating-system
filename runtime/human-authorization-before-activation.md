# Human Authorization Before Activation

## Purpose

Define human authorization requirements before any future controlled
activation.

## Mandatory authorization

Activation requires explicit human authorization for the specific action.

## Required scope fields

| Field | Requirement |
|---|---|
| `authorizer` | Human authorizer. |
| `PR number` | PR authorized when applicable. |
| `branch` | Branch authorized. |
| `head SHA` | Exact head SHA authorized. |
| `commit` | Exact commit or merge commit authorized when applicable. |
| `action` | Activation, merge, rollback, exception or other action. |
| `scope` | Exact scope. |
| `expiration/scope limit` | One-time use, expiration or bounded scope. |

## Prohibitions

- No implicit authorization.
- No reused authorization from prior PRs.
- No automatic activation.
- No activation from simulation pass alone.

## Required registry

Authorization must be recorded in the relevant decision, audit, readiness and
activation review records before activation can proceed.

## Relationship with execution authorization layer

Block 12 records human authorization in the execution authorization layer. Any
change to PR, branch, head SHA, commit, scope or action invalidates prior
authorization.
