# Preflight Checks

## Purpose

Define checks required before a dry-run simulation can start.

## Required checks

| Check | Required validation |
|---|---|
| Authorization posture | Human authorization requirement is known and no implicit authorization is assumed. |
| Readiness | Orchestration readiness scope is documented. |
| Evidence | Evidence plan and simulated evidence requirements are defined. |
| Audit | Audit plan and simulated audit fields are defined. |
| Rollback | Rollback playbook and simulated rollback path are defined. |
| Incident response | Incident response playbook and simulation triggers are mapped. |
| Prohibited actions | No real execution, services, agents, dependencies, permissions or secrets are introduced. |

## Blocking failures

Preflight fails and blocks dry-run when:

- Scope is missing or ambiguous.
- Authorization posture is missing.
- Readiness review is incomplete.
- Evidence, audit, rollback or incident response mapping is missing.
- Any proposed step requires real execution.
- Any prohibited action is detected.

## Output

Preflight output is recorded in `logs/PREFLIGHT_CHECK_LOG.md`.

## Relationship with pre-execution authorization

Preflight checks feed the Block 12 pre-execution authorization checklist.
Passing preflight does not authorize execution.
