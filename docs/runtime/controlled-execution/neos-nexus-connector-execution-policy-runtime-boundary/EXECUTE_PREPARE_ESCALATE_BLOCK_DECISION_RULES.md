# Execute, Prepare, Escalate, Block Decision Rules

## Rule order

Decisions are evaluated in this order: block conditions, authorization fit, data-class boundary, environment boundary, tool capability boundary, rollback posture, audit completeness, then execution permission. A single block condition overrides all other readiness signals.

## Execute

Execute only when the action is explicitly authorized and all scope fields match the request exactly. The authorization must name the connector or connector class, permitted tool behavior, target environment, action type, data class, risk tier, approver, valid time window, and rollback or recovery expectation.

Execution is never inferred from prior preparation, successful simulation, previous PR creation, documentation approval, or general program approval.

## Prepare

Prepare is allowed for documentation, local validation, draft payloads, dry-run plans, mock records, sandbox-only examples, checklists, and handoff packages when the work creates no external effect and uses no real restricted data.

Preparation must label any artifact as non-live when it could be mistaken for an execution instruction.

## Escalate

Escalate when intent is valid but authority is incomplete. Escalation is required for ambiguous accounts, mismatched branches, missing PR identifiers, missing Head SHA requirements, uncertain data classification, unverified recipient lists, unknown automation cadence, or any requested expansion beyond the approved boundary.

Escalation pauses the action and preserves context for a human decision.

## Block

Block actions that request production live activation, secrets, real credentials, real Drive access without approval, external communications, live automations, campaigns, C4-C7 data, CI runners, dependency installation, merge, auto-merge, deletion outside scope, or mutation outside the authorized path.

Blocked decisions must record the exact blocker and the lowest-risk allowable alternative, usually prepare-only documentation or a handoff note.

## Downgrade rules

If an execute request partially satisfies the boundary, downgrade it to prepare when a safe local artifact can be produced. Downgrade it to escalate when human authorization could make the action valid. Downgrade it to block when the action is categorically prohibited.
