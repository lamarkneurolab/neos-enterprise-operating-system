# Action Authority Matrix

## Purpose

This matrix defines the NEOS/NEXUS authority levels for action.

## Level 1 - Free Action

Level 1 actions are internal, reversible, low-risk, and expected to be executed without asking Tiziano for obvious microauthorization.

Allowed actions:

- Read.
- Analyze.
- Compare.
- Classify.
- Draft.
- Create internal drafts.
- Create internal documents.
- Create non-destructive scripts.
- Validate.
- Correct minor errors.
- Create branch.
- Commit.
- Push.
- Open PR.

## Level 2 - Supervised Resolutive Action

Level 2 actions are operational but bounded. They can be executed when the task scope authorizes them and no critical impact is introduced.

Allowed actions:

- Organize documents within authorized scope.
- Create non-critical internal folders.
- Prepare draft campaigns.
- Prepare draft proposals.
- Prepare draft WhatsApp responses.
- Create disabled n8n flows.
- Create non-live agents.
- Prepare mock or limited connectors.
- Update non-critical documentation within scope.

## Level 3 - Critical Action

Level 3 actions require explicit human authorization before execution.

Critical actions:

- Merge.
- Delete.
- Move source mother documents.
- Share documents.
- Change permissions.
- Publish.
- Send external communications.
- Send final proposals.
- Send invoices.
- Activate campaigns.
- Connect credentials.
- Use secrets.
- Activate production.
- Activate live agents.
- Activate live automations.
- Touch C4-C7 data.
- Modify sensitive psychological data.
- Touch the local PC outside authorized scope.

## Decision Rule

If an action is ambiguous between levels, classify it at the higher level and request authorization.

## Status

Version: v0.1.0
Scope: documentary authority matrix
Execution status: non-live
