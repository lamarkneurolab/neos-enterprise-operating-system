# Lamark Pilot Sandbox Rollback Triggers

## Purpose

This document defines rollback triggers for Lamark sandbox preparation.

## Rollback Triggers

Sandbox preparation must stop and roll back to the last reviewed documentary state if any of the following occur:

- Real document movement occurs without authorization.
- Real document deletion occurs without authorization.
- Real document sharing occurs without authorization.
- Information is sent without authorization.
- Permissions are modified without authorization.
- Real documents are transformed without authorization.
- Sensitive financial data is introduced.
- Real customer data is introduced.
- Production activation is attempted.
- Runtime execution is attempted.
- External integration, agent, runner, CI, database, or service creation is attempted.
- Evidence records cannot be correlated to audit records.
- Human authorization is missing, expired, or out of scope.

## Rollback Evidence

Each rollback trigger must produce an evidence record that identifies the trigger, affected scope, reviewer, decision, and follow-up requirement.

## Status

Version: v0.1.0
Execution status: blocked
