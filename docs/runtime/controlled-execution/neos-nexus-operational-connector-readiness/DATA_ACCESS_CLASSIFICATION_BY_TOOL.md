# Data Access Classification By Tool

## Purpose

This document defines data access classes for NEOS/NEXUS connector readiness and maps which classes each tool may touch under controlled conditions.

C4-C7 require explicit human authorization.

## Data Classes

| Class | Name | Description | Default Handling |
| --- | --- | --- | --- |
| C0 | Public | Public material intended for open viewing. | May be read and analyzed when in scope. |
| C1 | Internal operational | Non-sensitive internal operating notes, checklists, docs, and process references. | May be used for internal work when in scope. |
| C2 | Commercial general | General commercial strategy, positioning, non-sensitive sales materials, and market notes. | May be drafted and analyzed when in scope. |
| C3 | Cliente/prospecto no sensible | Non-sensitive prospect or client context approved for operational use. | May be analyzed or drafted against only when authorized. |
| C4 | Financiero/comercial sensible | Financial records, invoices, pricing exceptions, contracts, sensitive deal terms, billing, and payment context. | Requires explicit human authorization. |
| C5 | Psicologico/corporativo sensible | Sensitive organizational psychology, internal behavioral, leadership, conflict, or people-related material. | Requires explicit human authorization. |
| C6 | Credenciales/secrets | API keys, tokens, passwords, private credentials, signing keys, and secret configuration. | Requires explicit human authorization and approved secret handling. |
| C7 | Produccion critica | Production systems, live automations, protected runtime state, production databases, deployment controls, and critical infrastructure. | Requires explicit human authorization and production controls. |

## Tool Classification Map

| Tool | C0 | C1 | C2 | C3 | C4 | C5 | C6 | C7 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| GitHub / local Codex | Allowed | Allowed | Allowed if in repo scope | Avoid unless explicitly scoped | Authorization required | Authorization required | Authorization required | Authorization required |
| Google Drive / NEXUS | Allowed if in scope | Allowed if in scope | Allowed if in scope | Authorization required | Authorization required | Authorization required | Authorization required | Authorization required |
| Gmail or Spacemail | Allowed if in scope | Allowed if in scope | Allowed if in scope | Authorization required | Authorization required | Authorization required | Authorization required | Authorization required |
| Google Calendar | Allowed if in scope | Allowed if in scope | Allowed if in scope | Authorization required | Authorization required | Authorization required | Authorization required | Authorization required |
| Notion | Allowed if in scope | Allowed if in scope | Allowed if in scope | Authorization required | Authorization required | Authorization required | Authorization required | Authorization required |
| Bigin / Zoho CRM | Allowed if in scope | Allowed if in scope | Allowed if in scope | Authorization required | Authorization required | Authorization required | Authorization required | Authorization required |
| Zoho Books | Avoid unless public docs | Internal process docs only | Finance drafts only if non-sensitive | Not applicable unless approved | Authorization required | Authorization required if present | Authorization required | Authorization required |
| n8n | Allowed for public docs | Allowed for workflow docs | Allowed for non-live workflow plans | Authorization required | Authorization required | Authorization required | Authorization required | Authorization required |
| WhatsApp | Allowed if in scope | Allowed if in scope | Allowed if in scope | Authorization required | Authorization required | Authorization required | Authorization required | Authorization required |
| OpenAI / Claude API | Allowed | Allowed if non-sensitive | Allowed if non-sensitive | Authorization required | Authorization required | Authorization required | Authorization required | Authorization required |
| Future NEXUS Console | Allowed for design | Allowed for design | Allowed for design | Authorization required | Authorization required | Authorization required | Authorization required | Authorization required |

## Authorization Rule

NEOS/NEXUS may not touch C4, C5, C6, or C7 data without explicit human authorization.

Authorization must define:

- Tool.
- Data class.
- Data source.
- Intended action.
- Operational scope.
- Expected output.
- Whether the action is read-only, draft-only, controlled execution, critical, or live.

## Block 28 Boundary

Block 28 does not grant access to C4-C7 data. It only documents the classification model required before future connector use.
