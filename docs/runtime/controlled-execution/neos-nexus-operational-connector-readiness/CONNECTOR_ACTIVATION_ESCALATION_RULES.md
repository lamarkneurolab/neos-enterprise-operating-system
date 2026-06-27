# Connector Activation Escalation Rules

## Purpose

This document defines which connector actions escalate to Tiziano and which actions may proceed without microauthorization when they remain within an authorized technical scope.

Block 28 does not authorize live production, secrets, sensitive data access, external communications, campaigns, automations, permission changes, or merge.

## Actions That Escalate To Tiziano

The following actions require explicit human authorization before execution:

- Merge to main.
- Delete files.
- Move source-of-truth material.
- Share documents.
- Change permissions.
- Publish content.
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
- Touch the local PC outside the authorized scope.

## Actions That Do Not Require Microauthorization

The following actions may proceed without repeated microauthorization when they stay inside the authorized task scope and do not touch critical systems or sensitive data:

- Read authorized files.
- Analyze authorized context.
- Compare documents or repository state.
- Classify non-sensitive materials.
- Draft internal content.
- Create internal documents.
- Create non-destructive scripts.
- Validate with local checks.
- Correct minor errors within scope.
- Create a branch.
- Commit scoped changes.
- Push the scoped branch.
- Open a pull request.

## Critical Authorization Standard

When escalation is required, approval must be explicit and specific. The approval should identify:

- The exact tool.
- The exact action.
- The target record, file, branch, document, system, or connector.
- The expected impact.
- Whether the action touches C4-C7 data.
- For merge requests, the PR number and exact head SHA.

Merge remains prohibited unless Tiziano authorizes the exact PR number and exact head SHA.

## Block 28 Enforcement

During Block 28:

- No production live activation is allowed.
- No credentials or secrets may be introduced.
- No external communications may be sent.
- No campaigns may be activated.
- No live automations may be activated.
- No permissions may be modified.
- No Google Drive files may be moved, deleted, shared, or permission-modified.
- No C4-C7 data may be touched.
- No changes may occur outside the authorized documentation route.
