# Connector Readiness Overview

## Purpose

Block 28 defines the readiness map for the real tools that NEOS and NEXUS may use to support Lamark operations with controlled execution capacity.

This block prepares the operational connector model without enabling live production, exposing credentials, touching sensitive data, changing permissions, sending communications, activating campaigns, or activating live automations.

The objective is to distinguish technical availability from operational authority before any connector is used in a resolving workflow.

## Core Principle

Disponibilidad tecnica no equivale a autorizacion operativa.

A tool may exist in the environment and still be unavailable for execution. NEOS and NEXUS must treat every connector through separate readiness states:

| State | Meaning |
| --- | --- |
| Available | The tool exists as a possible system capability or integration target. |
| Connected | The tool has a configured connection path or account-level access route. |
| Authorized | Tiziano or the applicable human authority has approved a defined scope of use. |
| Executable | NEOS/NEXUS may perform controlled actions within the authorized scope. |
| Live | The tool can affect production systems, external parties, money, permissions, campaigns, automations, or sensitive records. |

Available, connected, authorized, executable, and live are not interchangeable. Each state must be evaluated independently.

## Primary Connector Map

| Connector | Readiness Role | Block 28 Position |
| --- | --- | --- |
| GitHub / local Codex | Repository editing, validation, branch creation, commit, push, and PR preparation. | Controlled execution is allowed for non-critical technical work; merge is not authorized. |
| Google Drive / NEXUS | Knowledge documents, internal operating references, and future structured source material. | Readiness mapping only; no moving, deleting, sharing, or permission changes. |
| Gmail or Spacemail | Internal and external email workflows. | Drafting may be prepared; sending external communications is blocked without explicit authorization. |
| Google Calendar | Scheduling, coordination, availability, and meeting records. | Read-only and draft preparation only unless explicitly authorized. |
| Notion | Knowledge management, planning, operational documentation, and task structure. | Internal draft and documentation use only; no live permissions or sensitive data changes. |
| Bigin / Zoho CRM | Commercial pipeline, prospects, deals, and customer-facing records. | Readiness mapping only; customer-impacting updates require authorization. |
| Zoho Books | Billing, invoices, financial records, and payment-related workflows. | Critical by default; invoice or financial actions require explicit authorization. |
| n8n | Workflow automation and connector orchestration. | Design and non-live drafts only; live automations are blocked in Block 28. |
| WhatsApp | Client, prospect, partner, and operational messaging. | Drafting only; sending or automating messages is blocked without explicit authorization. |
| OpenAI / Claude API | Analysis, drafting, classification, assisted reasoning, and future agentic workflows. | Non-sensitive analysis and draft generation only; secrets and live agents are blocked. |
| Future NEXUS Console | Central operating interface for connector state, approvals, logs, and execution controls. | Future readiness target; no production console activation in Block 28. |

## Operational Boundary

Block 28 prepares a map, not a live runtime. Its outputs are internal Markdown documents that define readiness, execution modes, data boundaries, and escalation rules for later implementation.

No connector is activated for production as part of this block.
