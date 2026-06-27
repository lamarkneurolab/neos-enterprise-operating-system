# Tool Execution Capability Matrix

## Purpose

This matrix defines what NEOS/NEXUS may do with each operational tool before live production is authorized.

The default rule is conservative: reading, analyzing, classifying, drafting, validating, creating internal documents, creating non-destructive scripts, creating branches, committing, pushing, and opening pull requests are allowed when they stay within the authorized scope. Critical actions require explicit human authorization.

## Capability Matrix

| Tool | Reading | Analysis | Drafting | Controlled Execution | Critical Action | Live State | Authorization Required |
| --- | --- | --- | --- | --- | --- | --- | --- |
| GitHub / local Codex | Allowed for repo context and status. | Allowed for diffs, validations, and technical review. | Allowed for docs, code proposals, PR descriptions, and internal plans. | Allowed for branch, commit, push, PR, non-destructive validation. | Merge to main, destructive changes, secrets, permissions, protected settings. | Not live by default. | Human approval required for merge, permissions, secrets, destructive actions, or production-affecting changes. |
| Google Drive / NEXUS | Allowed only within authorized files and folders. | Allowed for internal classification and comparison. | Allowed for internal document drafts. | Blocked in Block 28 for moving, deleting, sharing, or permission changes. | Sharing, permission changes, moving source-of-truth files, deletion. | Blocked. | Human approval required for sharing, permission, movement, deletion, or sensitive data. |
| Gmail or Spacemail | Allowed only where mailbox access is explicitly available and in scope. | Allowed for thread analysis and response preparation. | Allowed for draft messages. | Sending is blocked unless explicitly authorized. | External communications, final offers, commitments, sensitive disclosures. | Blocked. | Human approval required for sending, forwarding, external replies, or sensitive content. |
| Google Calendar | Allowed for authorized calendar context. | Allowed for availability and scheduling analysis. | Allowed for proposed events and agenda drafts. | Event creation or updates require explicit scope approval. | External invitations, calendar permission changes, sensitive scheduling. | Blocked. | Human approval required for live event changes and external invites. |
| Notion | Allowed for authorized workspace content. | Allowed for knowledge organization and task analysis. | Allowed for internal pages, plans, and specs. | Controlled internal updates may be allowed when non-sensitive and scoped. | Permission changes, public publishing, sensitive operational records. | Blocked. | Human approval required for permission, publishing, or C4-C7 content. |
| Bigin / Zoho CRM | Allowed only after authorized connector access. | Allowed for pipeline and customer/prospect analysis. | Allowed for note, proposal, and follow-up drafts. | Live CRM updates blocked in Block 28. | Customer record changes, deal stage changes, outbound actions. | Blocked. | Human approval required for customer-impacting updates or C4-C7 data. |
| Zoho Books | Readiness mapping only in Block 28. | Allowed only on non-sensitive synthetic or approved summaries. | Allowed for invoice or finance draft preparation. | Blocked. | Invoices, billing, payments, tax records, financial records. | Blocked. | Human approval required for all billing and financial actions. |
| n8n | Allowed for workflow design files and non-live specs. | Allowed for workflow risk analysis. | Allowed for automation drafts and pseudocode. | Non-live scripts or diagrams only. | Activating workflows, production credentials, live triggers. | Blocked. | Human approval required for credentials, triggers, production execution, and live automations. |
| WhatsApp | Readiness mapping only unless authorized. | Allowed for communication strategy and draft analysis. | Allowed for message drafts. | Sending is blocked. | External messages, automated messaging, sensitive disclosures. | Blocked. | Human approval required for any live message or automation. |
| OpenAI / Claude API | Allowed for non-sensitive prompt and output analysis. | Allowed for classification, reasoning, drafting, and validation. | Allowed for internal drafts and non-sensitive artifacts. | Controlled use allowed only without secrets and without C4-C7 data. | Secrets, sensitive data, live agents, autonomous production action. | Blocked for live agents. | Human approval required for secrets, C4-C7 data, live agents, or production execution. |
| Future NEXUS Console | Conceptual readiness only. | Allowed for control-plane design. | Allowed for internal console specs. | Blocked until implemented and authorized. | Production controls, connector activation, approval state changes. | Blocked. | Human approval required before any production console use. |

## Actions Allowed Without Microauthorization

When already inside the authorized task scope, NEOS/Codex may:

- Read authorized repo files and internal documents.
- Analyze, compare, classify, and summarize.
- Draft internal documents, scripts, matrices, and operating procedures.
- Create non-destructive scripts.
- Validate with local checks.
- Correct minor errors inside the authorized scope.
- Create branches.
- Commit scoped changes.
- Push scoped branches.
- Open pull requests.

## Actions Requiring Human Authorization

The following require explicit human approval:

- Merge to main.
- Change permissions.
- Use or connect secrets.
- Touch production systems.
- Send external communications.
- Send final proposals.
- Send invoices or billing actions.
- Activate campaigns.
- Activate live automations.
- Activate live agents.
- Touch C4-C7 data.
- Perform destructive changes such as deletion or source-of-truth movement.
