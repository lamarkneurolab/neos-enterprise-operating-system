# Permission Registry

Canonical registry for actions that require human authorization.

| ID | Permission | Description | Applies To | Human Authorization | Evidence Requirement | Status |
|---|---|---|---|---|---|---|
| permission.repo.create_branch | `repo.create_branch` | Create repository branch | Git repositories | Required | Branch name and status output | Active |
| permission.repo.write | `repo.write` | Create, update or delete repository files | Git repositories | Required | Diff summary and commit hash | Active |
| permission.repo.commit | `repo.commit` | Commit staged repository changes | Git repositories | Required | Commit hash and commit message | Active |
| permission.repo.push | `repo.push` | Push commits to a remote repository | Git remotes | Required | Remote branch and push output | Active |
| permission.repo.open_pr | `repo.open_pr` | Open pull request | GitHub | Required | Pull request URL | Pending authorization |
| permission.workflow.update | `workflow.update` | Create or update GitHub Actions workflows | GitHub | Required with workflow-scoped credential | Commit hash and push output | Pending authorization |
| permission.external.publish | `external.publish` | Publish content to a non-GitHub external system | External connectors | Required | External URL or record ID | Draft |

## Authorization rules

- Authorization must be explicit in the user conversation or an approved policy.
- Missing credential scope blocks execution even when the local change is valid.
- Approval for one permission does not imply approval for unrelated permissions.
