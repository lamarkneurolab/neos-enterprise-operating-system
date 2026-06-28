# Unauthorized Action Stop Conditions

## Purpose

These conditions require NEOS/NEXUS to stop before connector execution.

## Stop Conditions

- No explicit human authorization exists.
- Authorization does not name the exact connector, account, environment, object, or action.
- The requested action exceeds the approved scope.
- The authorization is expired, revoked, contradicted, or unclear.
- Data class is unknown or includes prohibited C4-C7 handling.
- The action would expose secrets or credentials.
- The action would trigger production, live automation, campaign activity, external communication, permission change, Drive mutation, merge, or auto-merge without exact approval.
- Rollback or irreversibility evidence is missing for a critical action.
- Required PR number or exact Head SHA is missing for merge-related action.

## Allowed Continuation

After stopping, NEOS/NEXUS may prepare a non-live handoff that identifies the missing approval and exact evidence needed.
