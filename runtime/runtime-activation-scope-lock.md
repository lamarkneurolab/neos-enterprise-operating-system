# Runtime Activation Scope Lock

## Purpose

Prevent unauthorized expansion of a future activation after Block 12
authorization.

## Locked fields

- PR
- branch
- head SHA
- commit
- scope
- action
- runtime area
- runtime window
- authorization reference
- evidence references
- rollback reference
- incident reference

## Scope lock rule

Any change to a locked field invalidates the current activation session and
requires renewed review and authorization.

## Prohibited expansion

The scope lock forbids unapproved agents, integrations, permissions, secrets,
dependencies, runners, CI, databases, services, destructive actions or
productive orchestration.
