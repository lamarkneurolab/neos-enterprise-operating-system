# Local Machine Access Model

## Purpose

This model defines the NEOS Local Operator Layer for controlled local workstation operation.

## Local Components

- NEOS Local Operator Layer: the local operating boundary for authorized machine work.
- Codex Local Operator: the technical operator that can execute local repo, file, and validation tasks within scope.
- Drive Local Sync: local read path for authorized NEXUS/Drive material when available.
- GitHub Local Repo: the canonical local checkout used for NEOS implementation work.
- Logs: local execution evidence and healthcheck outputs.
- Backups: local backup area for authorized reversible preparation.
- Policies: local action policy, access matrix, and critical action rules.
- Healthcheck: local script that reports tools, folders, repo state, and Drive detection.

## Local Machine Modes

`LOCAL_MACHINE_MODE = disabled / supervised / authorized_session / live_operator`

| Mode | Meaning |
|---|---|
| disabled | No local machine operation is available or authorized |
| supervised | Internal reversible actions are allowed inside authorized paths |
| authorized_session | A specific local operating session is authorized with defined boundaries |
| live_operator | Live local operation is enabled for defined tools and scope |

## Access Rules

No local access is promised if no technical channel is installed.

Once installed, the local operator may work only in authorized routes, such as `~/NEOS_LOCAL_OPERATOR`, the authorized NEOS repo, and explicitly approved local folders.

Critical local actions require authorization. Destructive commands require authorization. Installations with elevated permissions require authorization.

## Boundaries

The local operator must not touch personal folders, official Drive source folders, credentials, secrets, keychains, permissions, live services, or production systems without explicit authorization.

## Status

Version: v0.1.0
Scope: documentary local access model
Execution status: non-live
