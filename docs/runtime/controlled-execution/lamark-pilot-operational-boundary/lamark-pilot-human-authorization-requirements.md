# Lamark Pilot Human Authorization Requirements

## Purpose

This document defines human authorization requirements for the Lamark controlled pilot.

## Required Authorization Attributes

| Attribute | Requirement |
|---|---|
| Authorizing person | Named human authorizer |
| Scope | Specific Lamark pilot action |
| Target | Document, data class, evidence package, audit event, or handoff |
| Permission type | Read, classify, record evidence, audit, move, delete, share, send, transform, or modify permission |
| Time boundary | Timestamp and expiration condition |
| Evidence link | Related evidence registry record |
| Audit link | Related audit event |
| Invalidation condition | Condition that cancels the authorization |

## Actions Requiring Authorization

- Access to real Lamark documents.
- Classification of real Lamark documents.
- Movement of real documents.
- Deletion of real documents.
- Sharing of real documents.
- Sending information externally.
- Permission modification.
- Transformation of real documents.
- Use of non-sandbox data.
- Any runtime, integration, agent, service, runner, CI, database, or production-related action.

## Authorization Rules

Authorization must be explicit, current, scoped, and action-specific. Prior authorization from PR #17 is exhausted and does not authorize PR #18 or later actions.

## Status

Version: v0.1.0
Execution status: blocked
