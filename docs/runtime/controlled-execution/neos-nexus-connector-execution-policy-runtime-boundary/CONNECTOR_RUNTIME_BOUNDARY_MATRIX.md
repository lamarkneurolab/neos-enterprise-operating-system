# Connector Runtime Boundary Matrix

| Connector class | Prepare allowed | Execute allowed | Escalate when | Block when |
| --- | --- | --- | --- | --- |
| GitHub | Draft branches, commits, PR text, review notes, audit checklists. | Creating bounded branches, commits, or PRs when authorized. | PR target, Head SHA, repository, branch, or review expectation is unclear. | Merge, auto-merge, destructive reset, CI runner activation, or unauthorized repository mutation is requested. |
| Google Drive | Draft file plans, mock folder maps, document templates, non-live metadata examples. | Updating approved documents or folders only inside the named account, file, and scope. | File identity, sharing boundary, data class, or owner authority is uncertain. | Real Drive access is unapproved, restricted data appears, sharing is broadened, or credentials are requested. |
| Communications | Draft messages, prepare templates, classify recipients, assemble approval packets. | Send only with exact recipient, channel, content, and approval record. | Recipient list, message body, sender identity, or legal/compliance review is incomplete. | External communication is unapproved, sensitive data is included, or campaign-like outreach is requested. |
| Automations | Draft schedules, mock triggers, dry-run runbooks, disablement plans. | Enable only bounded, reversible, approved automation in the named environment. | Cadence, end condition, blast radius, or operator ownership is missing. | Live automation is unapproved, unbounded, self-expanding, or capable of external mutation. |
| Campaigns | Prepare non-live planning docs, mock creative, budget templates. | Execute only when campaign activation authority is explicitly granted. | Budget, account, identity, creative approval, or billing status is incomplete. | Real campaigns, spend, billing, or activation are requested without explicit approval. |
| Local tooling | Validate paths, build docs, inspect repository state, prepare evidence. | Execute local write operations only inside scoped paths. | Tool side effects or filesystem scope are uncertain. | Secrets, dependency downloads, live services, CI, or out-of-scope writes are required. |

## Matrix use

The matrix establishes the runtime ceiling for each connector class. A lower-risk decision may always be selected. A higher-risk decision requires an exact authorization match and complete audit evidence.

## Data boundary overlay

C0-C2 data may support prepare work when it is public, synthetic, or operationally non-sensitive. C3 data requires explicit scope confirmation. C4-C7 data is blocked unless a separate, named authorization grants a compliant handling path.
