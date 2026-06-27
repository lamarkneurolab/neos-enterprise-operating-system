# Lamark Internal Production Tool Map

## Purpose

This map identifies which tools may support each Lamark internal area once connector readiness is reviewed. It does not activate any tool live.

Block 28 maps operational fit only. Production use, live automation, sensitive-data access, permissions, secrets, external communications, campaigns, and billing actions remain blocked unless explicitly authorized.

## Area Tool Map

| Lamark Area | Supporting Tools | Support Role | Block 28 Position |
| --- | --- | --- | --- |
| Strategy | Notion, Google Drive / NEXUS, OpenAI / Claude API, future NEXUS Console | Strategic documents, operating doctrine, decision records, synthesis, and planning. | Internal documentation and analysis only. |
| Commercial | Bigin / Zoho CRM, Gmail or Spacemail, WhatsApp, Google Calendar, Notion | Pipeline context, prospect notes, proposal drafts, follow-up planning, meeting coordination. | Drafting and mapping only; no customer-impacting updates or sends. |
| Marketing | Notion, Google Drive / NEXUS, n8n, OpenAI / Claude API, future NEXUS Console | Campaign planning, content calendars, audience analysis, automation design, review workflows. | No campaign activation or live automation. |
| Content | Google Drive / NEXUS, Notion, OpenAI / Claude API, Gmail or Spacemail | Drafting, editing, classification, knowledge reuse, and publication preparation. | Internal drafts only; no publishing or external distribution. |
| Finance | Zoho Books, Google Drive / NEXUS, Notion | Invoice drafts, financial operating notes, internal reconciliation support, billing workflow design. | No invoices, billing sends, payment changes, or financial record modifications. |
| Operations | Google Calendar, Google Drive / NEXUS, Notion, n8n, future NEXUS Console | Scheduling, SOPs, operational checklists, workflow coordination, controlled execution logs. | Non-live planning and internal docs only. |
| Psicologia corporativa | Google Drive / NEXUS, Notion, OpenAI / Claude API | Sensitive organizational psychology frameworks, internal reflection materials, and controlled knowledge organization. | Sensitive data is protected; C5 requires explicit human authorization. |
| NEXUS Knowledge Management | Google Drive / NEXUS, Notion, future NEXUS Console, OpenAI / Claude API | Source organization, retrieval structures, controlled knowledge surfaces, metadata, and synthesis. | No moving source-of-truth files, sharing, deletion, or permission changes. |
| NEOS Runtime / DevOps | GitHub / local Codex, OpenAI / Claude API, future NEXUS Console, n8n | Repository changes, validations, PRs, execution policy, runtime design, future orchestration. | Branch, commit, push, and PR allowed; merge and production are blocked. |
| Automation | n8n, future NEXUS Console, OpenAI / Claude API, Google Drive / NEXUS | Workflow specs, trigger design, approval gates, logging model, failure handling. | Draft and design only; live automations are blocked. |

## Non-Activation Statement

No tool listed in this map is activated live by this document.

This map is an internal readiness artifact for future controlled execution design and authorization review.
