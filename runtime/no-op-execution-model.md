# No-Op Execution Model

## Purpose

Define how no-op execution is represented for documentary simulation.

## Model

No-op execution records intended steps, expected state transitions and
simulated outcomes while preventing real execution.

## Prohibited side effects

No-op must not:

- Modify real runtime state.
- Call external integrations.
- Create agents.
- Create services, databases, runners, workers or queues.
- Change permissions.
- Manage secrets.
- Install dependencies.
- Delete files.
- Execute destructive actions.
- Activate productive orchestration.

## Real state rule

Real state is not modifiable by no-op. Any proposed mutation must be recorded
as simulated intent only.

## Simulated intent record

Each no-op step must record:

- Step ID.
- Intended action.
- Expected simulated result.
- Blocker condition.
- Evidence requirement.
- Audit requirement.
- Rollback expectation.

## Simulated result

No-op result may be `simulated_success`, `simulated_failure`,
`simulated_blocked` or `simulated_inconclusive`.

## Mandatory blockers

No-op is blocked when a step requires real credentials, external activation,
permission changes, secrets, dependencies, services, agents or destructive
actions.

## Relationship with activation authorization

No-op review may inform activation scope, but no-op success does not authorize
execution. Any future execution requires the controlled activation gate and
explicit human authorization.
