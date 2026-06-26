# Activation Scope Definition

## Purpose

Define exact scope requirements for controlled activation requests.

## Required scope

- Functional limits.
- Technical limits.
- Exclusions.
- Affected runtime areas.
- Linked PR.
- Linked branch.
- Linked head SHA.
- Linked commit.
- Requested action.

## Documentary dependencies

- Dry-run result.
- Simulation evidence.
- Audit entry.
- Rollback plan.
- Incident plan.
- Risk acceptance record.
- Human approval record.

## Prohibited actions

- Productive orchestration without explicit future authorization.
- Agent creation.
- External integration activation.
- Runner, CI, database or service creation.
- Permission changes.
- Secret management.
- Dependency installation.
- File deletion or destructive changes.

## Rule

Scope ambiguity blocks activation review.
