# Connector Registry

Canonical registry for external systems connected to NEOS.

| ID | Connector | Purpose | Source of Truth Role | Owner Layer | Risk Level | Authorization | Evidence Requirement | Status |
|---|---|---|---|---|---|---|---|---|
| connector.github | GitHub | Canonical repository and version control | Primary | DevOps Layer | High | `permission.repo.write` for write operations | Commit hash, branch name or PR URL | Active read; write pending authorization |
| connector.google-drive | Google Drive | Visual and documentary mirror | Secondary | Memory & Knowledge Layer | Medium | Human approval before sync or publication | Mirror path or synced document link | Draft |

## Record rules

- A connector must declare whether it is primary, secondary or non-canonical.
- A secondary connector must never override GitHub as source of truth.
- External publication or synchronization requires evidence.
