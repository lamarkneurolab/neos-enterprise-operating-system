# Lamark Pilot Rollback Boundaries

## Purpose

This document defines rollback boundaries for the Lamark controlled pilot.

## Rollback Triggers

| Trigger | Required Response |
|---|---|
| Unauthorized real document access | Stop activity, record incident, audit event, and evidence |
| Sensitive information exposure | Stop activity, isolate scope, record incident, and require human review |
| Unauthorized document movement | Stop activity and require rollback review |
| Unauthorized document deletion | Escalate as blocking incident and require recovery review |
| Unauthorized sharing or sending | Stop activity, record disclosure incident, and require human review |
| Permission modification attempt | Stop activity and block further execution review |
| Sandbox boundary escape | Stop activity and require boundary review |
| Evidence or audit gap | Hold readiness review until resolved |

## Rollback Restrictions

Rollback evidence does not authorize rollback execution by implication. Any real rollback affecting real documents, permissions, data, services, or production requires explicit human authorization.

## Review Requirements

Rollback review must record trigger, scope, related evidence, related audit event, human reviewer, required remediation, and post-rollback evidence.

## Status

Version: v0.1.0
Execution status: blocked
