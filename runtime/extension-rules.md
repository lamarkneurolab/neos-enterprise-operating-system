# Runtime Extension Rules

Extension Rules define how future SDK contracts, integration contracts and
internal interfaces may be added without weakening NEOS execution governance.

## Extension principles

- Extend documented contracts; do not bypass them.
- Link every extension to authorization, task, event, state, evidence, audit,
  incident and rollback records when applicable.
- Keep GitHub as canonical source and Markdown as official source format.
- Treat Google Drive only as visual or documentary mirror.
- Block external execution unless separately authorized.

## Required extension record

| Field | Requirement |
|---|---|
| `extension_id` | Unique extension identifier. |
| `contract_id` | SDK or integration contract being extended. |
| `version` | Proposed contract version. |
| `owner` | Human or governance actor requesting extension. |
| `purpose` | Reason for extension. |
| `compatibility_impact` | Backward compatible, additive or breaking. |
| `risk_level` | Low, medium, high or critical. |
| `authorization_ref` | Authorization reference. |
| `evidence_ref` | Evidence reference. |
| `audit_ref` | Audit reference when required. |
| `rollback_ref` | Rollback rule or reference. |

## Allowed extensions

| Extension type | Rule |
|---|---|
| Additive field | Allowed in patch or minor version when optional and documented. |
| New SDK contract | Allowed when template fields are complete. |
| New integration entry | Allowed when external boundary and authorization rules are explicit. |
| New internal interface | Allowed when origin, destination, data, event, state and controls are complete. |
| New evidence rule | Allowed when it increases traceability. |
| New audit rule | Allowed when it increases governance reviewability. |

## Restricted extensions

| Extension type | Required control |
|---|---|
| External execution | Explicit human authorization and boundary review. |
| Destructive action | Exact-action approval, rollback plan and evidence. |
| Permission change | Out of scope for Block 7; requires separate approved block. |
| Secret handling | Out of scope for Block 7; must not be introduced. |
| Business agent behavior | Out of scope for Block 7; must not be introduced. |
| Breaking contract change | Major version proposal, compatibility review and rollback rule. |

## Prohibited extensions

- Business agents.
- Commercial, clinical, documentation, marketing, sales or operations agents.
- Production connector execution.
- Hidden external side effects.
- Permission modification.
- Secret storage or transmission.
- Database creation.
- Dependency installation without explicit authorization.
- Automatic merge.

## Extension workflow

1. Identify the contract or interface to extend.
2. Classify risk and compatibility impact.
3. Confirm authorization requirement.
4. Update the contract document.
5. Update compatibility matrix.
6. Update evidence and audit logs when applicable.
7. Validate with `git diff --check` and file inspection.
8. Commit, push and open PR when authorized.
9. Do not merge without explicit authorization for the specific PR.

## Rollback

Preferred rollback for repository documentation extension:

```text
git revert <extension_commit_sha>
```

If the PR is not merged:

```text
Close the PR without merge.
```

If a contract version must be superseded:

1. Mark new version as superseded.
2. Restore previous compatible version reference.
3. Record evidence and audit.
4. Record incident if the change created a runtime risk.
