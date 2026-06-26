# Dry-Run Validation Scenarios

## Purpose

Define minimum validation scenarios for orchestration dry-run review.

## Minimum scenarios

| Scenario | Expected result |
|---|---|
| Valid dry-run | Preflight passes, simulated evidence and audit are sufficient and result is `PASS`. |
| Missing authorization | Dry-run is `BLOCKED`; no implicit authorization is assumed. |
| Missing evidence | Dry-run is `BLOCKED` until simulated evidence plan is complete. |
| Missing rollback | Dry-run is `BLOCKED` until rollback simulation path is defined. |
| Preflight failed | Dry-run does not start; failure is recorded. |
| Incident simulation triggered | Incident simulation records severity, response, evidence and blocker status. |
| Audit incomplete | Dry-run is `BLOCKED` or `INCONCLUSIVE` until simulated audit is sufficient. |
| Activation blocked | Simulation pass does not approve activation; activation remains blocked without specific authorization. |

## Required evidence

Each scenario must link simulated evidence, simulated audit and result registry
entries.

## Required audit

Scenario review must record simulated audit when it affects readiness,
activation posture, rollback or incident response.
