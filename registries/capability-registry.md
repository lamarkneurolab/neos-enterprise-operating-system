# Capability Registry

Canonical registry for normalized NEOS capability identifiers.

| Capability | Description | Owner Layer | Risk Level | Permission Reference | Evidence Requirement | Status |
|---|---|---|---|---|---|---|
| repository.read | Read repository metadata and files | DevOps Layer | Low | Not required for local read access | File path or command output summary | Active |
| repository.branch | Create or switch repository branches | DevOps Layer | Medium | `permission.repo.create_branch` | Branch name and status output | Active |
| repository.write | Create, update or delete repository files | DevOps Layer | High | `permission.repo.write` | Diff summary and commit hash | Pending authorization |
| repository.commit | Stage and commit repository changes | DevOps Layer | Medium | `permission.repo.commit` | Commit hash and commit message | Active |
| repository.pull_request | Open or update pull requests | DevOps Layer | Medium | `permission.repo.open_pr` | Pull request URL | Pending authorization |
| engineering.change | Modify code, documentation or configuration | DevOps Layer | Medium | Depends on target system | Diff summary and verification result | Active |
| devops.execution | Run commands for setup, validation or deployment | DevOps Layer | Medium/High | Depends on side effect and environment | Command output summary | Active |
| evidence.log | Register evidence for completed actions | Governance Layer | Low | Not required | Evidence log entry | Active |
| decision.record | Record governance decisions | Governance Layer | Low | Human approval for material decisions | Decision log entry | Active |
| architecture.orchestrate | Define system architecture and sequencing | Governance Layer | Medium | Human approval for material changes | ADR, roadmap or decision log entry | Active |
| governance.review | Review actions, records and decisions for compliance with NEOS rules | Governance Layer | Medium | Human approval for material governance changes | Decision log entry or review note | Active |

## Naming rules

- Capability IDs use lowercase dot notation.
- Capability IDs describe outcomes, not tools.
- New capabilities must define an owner layer before activation.
