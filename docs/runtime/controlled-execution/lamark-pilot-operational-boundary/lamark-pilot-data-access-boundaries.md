# Lamark Pilot Data Access Boundaries

## Purpose

This document defines data access boundaries for the Lamark controlled pilot.

## Allowed Data Access

| Data Category | Access Level | Conditions |
|---|---|---|
| Sandbox documents | Read and classify | Must be approved sandbox copies |
| Public non-sensitive reference material | Read | Must not include real customer or financial data |
| Approved metadata | Read-only | Must be explicitly approved for pilot planning |
| Evidence records | Read and create documentary records | Must remain in the official documentary scope |
| Audit records | Read and correlate | Must not grant execution permission |

## Restricted Data Access

| Data Category | Status |
|---|---|
| Sensitive financial data | Blocked |
| Real customer data | Blocked |
| External commercial diagnosis data | Blocked |
| Secrets, credentials, and tokens | Blocked |
| Production data | Blocked |
| Permission configuration data | Blocked for modification |
| Real documents not explicitly authorized | Blocked |

## Access Rules

Data access must be minimal, sandbox-first, and evidence-backed. Any expansion from sandbox data to real Lamark material requires explicit human authorization.

## Status

Version: v0.1.0
Execution status: blocked
