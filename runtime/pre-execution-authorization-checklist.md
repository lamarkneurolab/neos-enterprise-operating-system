# Pre-Execution Authorization Checklist

## Purpose

Define the checklist required before future execution authorization.

## Checklist

- [ ] Dry-run passed and reviewed.
- [ ] Simulated evidence is sufficient.
- [ ] Simulated audit is complete.
- [ ] Rollback is defined.
- [ ] Incident response mapping exists.
- [ ] Scope is exact.
- [ ] Head SHA is specific.
- [ ] PR is specific.
- [ ] Branch is specific.
- [ ] Commit is specific.
- [ ] Human authorization is explicit.
- [ ] Abort conditions are defined.
- [ ] No prohibited action is required.

## Blocking rule

If anything changed after approval, authorization is invalid and must be
reviewed again.
