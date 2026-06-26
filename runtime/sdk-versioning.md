# SDK Versioning

SDK Versioning defines the version and compatibility rules for Runtime SDK and
Integration Contracts.

## Version format

Contracts use semantic-style documentary versions:

```text
MAJOR.MINOR.PATCH
```

Block 7 baseline version:

```text
0.1.0
```

## Version classes

| Version change | Meaning | Required review |
|---|---|---|
| Patch | Clarifies wording or adds non-breaking evidence. | File inspection and evidence. |
| Minor | Adds optional contract fields, compatible contracts or compatible interfaces. | Compatibility matrix, evidence and audit. |
| Major | Removes fields, changes required behavior or breaks compatibility. | Explicit review, audit, incident risk review and rollback plan. |

## Compatibility statuses

| Status | Meaning |
|---|---|
| `compatible` | Existing modules can keep using the contract. |
| `compatible_with_review` | Existing modules can use the contract after review evidence. |
| `additive` | New optional capability or field, backward compatible. |
| `deprecated` | Contract remains readable but should not be used for new work. |
| `superseded` | New contract version replaces the old one. |
| `breaking` | Existing modules may fail or require migration. |
| `revoked` | Contract must not be used. |

## Required version record

| Field | Requirement |
|---|---|
| `contract_id` | SDK or integration contract identifier. |
| `previous_version` | Previous version or `n/a`. |
| `new_version` | Proposed or current version. |
| `change_type` | Patch, minor or major. |
| `compatibility_status` | Compatibility status. |
| `affected_modules` | Runtime modules affected. |
| `evidence_ref` | Evidence log reference. |
| `audit_ref` | Audit trail reference when required. |
| `rollback_rule` | Revert, supersede, revoke or close PR without merge. |

## Rules

- Versions must be documented before use.
- Breaking changes require explicit review before merge.
- Deprecated contracts must name the replacement contract when one exists.
- Revoked contracts must not be used for new runtime tasks.
- Compatibility must be reflected in `runtime/compatibility-matrix.md`.
- SDK and integration logs must record material version changes.

## Rollback

| Rollback type | Rule |
|---|---|
| Revert commit | Use `git revert <commit_sha>`. |
| Supersede version | Mark the new version as superseded and restore prior compatible version. |
| Revoke version | Mark unsafe version as revoked and record incident. |
| Close PR | Close unmerged PR without merge. |

Rollback must link evidence and audit when the version had governance impact.
