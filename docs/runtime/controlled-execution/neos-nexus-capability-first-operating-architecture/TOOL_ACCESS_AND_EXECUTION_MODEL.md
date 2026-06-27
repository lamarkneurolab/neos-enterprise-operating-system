# Tool Access and Execution Model

## Purpose

This model defines objective tool access for NEOS/NEXUS execution with human-controlled critical impact.

## Tool Domains

| Tool | Operating Purpose | Live Constraint |
|---|---|---|
| GitHub | NEOS implementation, version control, PR evidence, technical governance | Merge and protected actions require authorization |
| Google Drive | NEXUS documentary operation, authorized source review, evidence packages | Sharing, moving, deleting, and permission changes require authorization |
| Notion | Knowledge organization, task context, operating records | External publication or sensitive changes require authorization |
| Bigin / Zoho CRM | Commercial intake, pipeline records, draft follow-up | Client-impacting changes require authorization |
| Zoho Books | Estimates, invoices, billing records | Final invoices and financial changes require authorization |
| Spacemail / Gmail | Draft communications and inbox context | Sending external communications requires authorization |
| Calendar | Scheduling context and draft meeting operations | Invites or changes affecting others require authorization |
| n8n | Draft and disabled automation flows | Live workflow activation requires authorization |
| WhatsApp | Draft responses and supervised messaging flows | Live sending requires authorization |
| OpenAI API / Claude API | Model-backed drafting, analysis, and controlled internal execution | Live agents, secrets, and production use require authorization |
| Future NEXUS Console | Unified orchestration, evidence, switches, and operator control | Live switches require authorization |

## Governance Split

Drive/NEXUS governs documentary operation. GitHub/NEOS governs technical implementation.

Codex and the assistant may consult Drive when a block depends on NEXUS, provided the task scope authorizes reading and no source documents are moved, deleted, shared, or permission-modified.

## Live Switches

Live tool use requires explicit switches and authorization:

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
Scope: documentary tool access model
Execution status: non-live
