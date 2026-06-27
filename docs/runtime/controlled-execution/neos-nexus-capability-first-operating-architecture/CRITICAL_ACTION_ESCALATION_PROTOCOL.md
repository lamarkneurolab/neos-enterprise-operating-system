# Critical Action Escalation Protocol

## Purpose

This protocol defines when NEOS/NEXUS must stop and request authorization before critical action.

## Stop Conditions

Stop before any action that would merge, delete, move source mother documents, share documents, change permissions, publish, send external communications, send final proposals, send invoices, activate campaigns, connect credentials, use secrets, activate production, activate live agents, activate live automations, touch C4-C7 data, modify sensitive psychological data, or touch the local PC outside authorized scope.

## Authorization Request

An authorization request must include:

- Intended action.
- Target system or path.
- Expected impact.
- Reversibility.
- Evidence reviewed.
- Required switch values.
- Exact PR number and Head SHA for merges.
- Critical data class if applicable.
- Confirmation that no broader permission is implied.

## Evidence Registration

Evidence may include file paths, commit SHAs, PR URLs, command results, decision records, Drive references, logs, or screenshots when authorized.

## If Authorization Is Denied

Stop the action, preserve current state, record the denial, report the blocked outcome, and propose a safe alternative if one exists.

## If Authorization Is Approved

Execute only the authorized action, only within the stated scope, and only while the current state still matches the authorization conditions.

If any condition changes, stop and request renewed authorization.

## Execution Report

After execution, report:

- Action completed.
- Evidence produced.
- Final state.
- Deviations, if any.
- Whether authorization is exhausted.

## Authorization Exhaustion

Authorization is exhausted after the approved critical action is completed, denied, fails, or no longer matches the current state.

## Required Switches

- `PUBLICATION_MODE = draft / ready / live`
- `WHATSAPP_MODE = draft / supervised / live`
- `CLIENT_MODE = internal_lamark / external_client`
- `CONNECTOR_MODE = mock / limited / live`
- `CAMPAIGN_MODE = draft / approved / live`
- `DOCUMENT_MODE = read_only / managed / external_shared`
- `PSYCHOLOGY_DATA_MODE = aggregated / sensitive / restricted`
- `LOCAL_MACHINE_MODE = disabled / supervised / authorized_session / live_operator`

## Status

Version: v0.1.0
Scope: documentary escalation protocol
Execution status: non-live
