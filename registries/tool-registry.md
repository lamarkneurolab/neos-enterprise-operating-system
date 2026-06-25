# Tool Registry

Canonical registry for executable tools available to NEOS.

| ID | Tool | Capability | Owner Layer | Risk Level | Authorization | Evidence Requirement | Status |
|---|---|---|---|---|---|---|---|
| tool.github-connector | GitHub Connector | `repository.read`, `repository.write`, `repository.branch`, `repository.pull_request` | DevOps Layer | High | `permission.repo.write` for write operations | Commit hash, branch name or PR URL | Pending authorization |
| tool.codex | Codex | `engineering.change`, `repository.commit`, `devops.execution` | DevOps Layer | High | Human approval for repository writes and external side effects | Local diff, commit hash and command output summary | Active |
| tool.chatgpt | ChatGPT | `architecture.orchestrate`, `governance.review`, `decision.record` | Governance Layer | Medium | Human approval for material governance decisions | Decision log entry or approved plan | Active |

## Record rules

- Tools must map to one or more capabilities in `registries/capability-registry.md`.
- Tools that write to canonical systems must reference a permission in
  `registries/permission-registry.md`.
- Tool activation requires evidence that the tool can perform its stated role.
