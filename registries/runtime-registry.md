# Runtime Registry

Canonical registry for execution runtimes available to NEOS.

| ID | Runtime | Purpose | Owner Layer | Allowed Capabilities | Risk Level | Authorization | Evidence Requirement | Status |
|---|---|---|---|---|---|---|---|---|
| runtime.chatgpt-orchestrator | ChatGPT Orchestrator | Architecture, planning and governance orchestration | Governance Layer | `architecture.orchestrate`, `decision.record` | Medium | Human approval for material governance decisions | Decision log, ADR or approved plan | Active |
| runtime.codex-engineering | Codex Engineering Runtime | Engineering execution, commits, refactoring and DevOps | DevOps Layer | `engineering.change`, `repository.branch`, `repository.commit`, `devops.execution` | High | Human approval for repository writes and external side effects | Diff summary, command output and commit hash | Active |
| runtime.github-actions | GitHub Actions | Remote CI and repository automation | DevOps Layer | `devops.execution` | High | `permission.workflow.update` before workflow changes | Workflow run URL or status summary | Pending authorization |

## Runtime rules

- Runtimes must declare allowed capabilities before use.
- Runtimes cannot execute permissions that are not authorized.
- Remote runtimes require stronger evidence than local read-only actions.
