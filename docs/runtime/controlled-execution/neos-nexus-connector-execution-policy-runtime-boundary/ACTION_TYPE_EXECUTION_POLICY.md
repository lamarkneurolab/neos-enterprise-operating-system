# Action Type Execution Policy

## Read

Read actions are allowed only when the source, account, repository, file, or record is inside the approved scope. Reads that expose restricted data, credentials, private communications, billing details, or unrelated customer material require escalation or blocking.

## Draft

Draft actions are prepare-only by default. They may create local documents, mock payloads, templates, and review packets when they do not send, publish, sync, schedule, or mutate live state.

## Write

Write actions require exact target scope and rollback expectations. Local documentation writes inside the requested path may proceed as prepare work. Connector writes to external systems require explicit execute authority.

## Submit

Submit actions include PR creation, form submission, comment posting, document sharing, approval requests, and queueing a connector operation. Submit requires an authorization record naming the destination and expected external effect.

## Activate

Activation includes enabling automations, campaigns, live integrations, scheduled jobs, production flags, or recurring actions. Activation is blocked unless the authorization explicitly names the production boundary, owner, rollback plan, monitoring plan, and expiration.

## Merge

Merge and auto-merge are blocked unless the exact PR number and exact Head SHA are provided in a human authorization for that individual PR. Batch approval does not authorize merge across multiple PRs.

## Delete

Delete actions are blocked by default. Deletion requires a named target, backup or recovery posture, evidence record, and explicit human approval. Bulk deletion requires separate authorization per bounded set.

## Notify

Notifications and communications remain prepare-only until the channel, sender, recipient list, content, timing, and approval record are exact. Any real external notification without that record is blocked.
