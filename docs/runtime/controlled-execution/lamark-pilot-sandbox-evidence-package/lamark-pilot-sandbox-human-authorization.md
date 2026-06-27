# Lamark Pilot Sandbox Human Authorization

## Purpose

This document defines mandatory human authorization for the Lamark documentary sandbox.

## Authorization Requirement

Human authorization is mandatory before any action that could affect real documents, real data, permissions, external systems, customer-facing activity, production state, or information sending.

## Actions Requiring Authorization

Authorization is required before:

- Creating a sandbox copy from a real document.
- Using any non-synthetic data.
- Moving real documents.
- Deleting real documents.
- Sharing real documents.
- Sending information.
- Modifying permissions.
- Transforming real documents.
- Expanding pilot scope.
- Leaving the documentary sandbox.

## Authorization Record

Each authorization must record:

- Approver.
- Date.
- Scope.
- Action authorized.
- Evidence reference.
- Expiration or review condition.
- Explicit statement that authorization applies only to the named action.

## Non-Carryover Rule

Past authorization does not authorize future actions. Authorization from prior blocks, PRs, or merges is exhausted unless renewed explicitly.

## Status

Version: v0.1.0
Execution status: blocked
