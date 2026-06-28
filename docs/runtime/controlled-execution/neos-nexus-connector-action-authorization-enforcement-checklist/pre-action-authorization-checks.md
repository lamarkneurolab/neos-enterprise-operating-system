# Pre-Action Authorization Checks

## Purpose

These checks run before any connector-mediated action that could affect external systems, production state, permissions, communications, spend, automation, merge state, or restricted data.

## Checks

- Confirm the requesting human and approval source.
- Confirm the action is explicitly authorized, not inferred from prior work.
- Confirm the authorization has not expired or been revoked.
- Confirm the requested action matches the approved connector, account, environment, object, and data class.
- Confirm no broader action is hidden inside a smaller instruction.
- Confirm the operational mode permits execution rather than preparation only.
- Confirm rollback, disablement, or irreversibility is documented.
- Confirm evidence can be recorded without exposing secrets or restricted data.

## Stop Rule

Stop when authorization is absent, stale, ambiguous, contradicted, mismatched, or not tied to the exact action scope.
