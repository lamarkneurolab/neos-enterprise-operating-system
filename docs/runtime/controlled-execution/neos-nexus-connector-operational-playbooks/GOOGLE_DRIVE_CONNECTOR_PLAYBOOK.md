# Google Drive Connector Playbook

## Allowed preparation

Drive preparation may draft document structures, folder maps, naming schemes, migration checklists, metadata templates, and non-live examples. Preparation must use local or synthetic content unless a specific Drive file and data class are authorized.

## Execute boundary

Drive execution requires exact account context, file or folder identity, action type, sharing boundary, data class, and approver. The action must not broaden sharing, alter ownership, expose restricted data, or move content outside the approved folder tree.

## Required checks

Confirm file identity before any write. Confirm that content classification allows the requested operation. Confirm that the action is reversible or that a recovery copy exists when mutation is authorized.

## Escalation triggers

Escalate when file ownership, folder destination, sharing scope, data classification, editor identity, or approval source is unclear. Escalate any request to process real customer, clinical, financial, legal, personnel, or credential-like material.

## Block conditions

Block real Drive access without authorization, public sharing, restricted data handling, credential requests, irreversible deletion, cross-account movement, and any request to bypass access controls.

## Handoff evidence

The Drive handoff records document name, file or folder reference if authorized, intended operation, data classification, sharing boundary, reviewer, and next approval required.
