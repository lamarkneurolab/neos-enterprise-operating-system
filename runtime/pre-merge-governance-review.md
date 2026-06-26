# Pre-merge Governance Review

Pre-merge Governance Review is mandatory for every NEOS Fase 3 pull request.

It is a documentary review gate. It does not merge pull requests and does not
replace Tiziano's explicit authorization for the specific PR.

## Required review

| Area | Required check | Blocking condition | Evidence | Audit | Logs |
|---|---|---|---|---|---|
| Block alignment | Change is additive and compatible with Blocks 1-7. | Contradiction or undocumented override. | File inspection and compatibility matrix reference. | Required when alignment affects governance. | `GOVERNANCE_GATE_LOG.md` |
| Prohibited agents | No business, commercial, clinical, documentation, marketing, sales or operations agents are created. | Any prohibited agent is created or enabled. | Changed file list and diff inspection. | Required if violation occurs. | `INCIDENT_LOG.md` |
| Destructive change | No deletion, reset, overwrite or irreversible mutation without exact authorization. | Destructive action detected. | Git diff and command history. | Required for attempted or blocked destructive action. | `INCIDENT_LOG.md`, `AUDIT_TRAIL.md` |
| Permissions | No permission, role or scope changes. | Permission change detected. | Diff inspection. | Required if attempted. | `INCIDENT_LOG.md` |
| Secrets | No secrets are read, stored, rotated or administered. | Secret handling detected. | Diff inspection and command evidence. | Required if attempted. | `INCIDENT_LOG.md` |
| Dependencies | No dependency installation without explicit authorization. | Dependency install or lockfile churn without authorization. | Command evidence and diff inspection. | Required if attempted. | `INCIDENT_LOG.md` |
| Markdown validity | Source remains Markdown `.md`. | Required Markdown file missing or invalid enough to block review. | File list and inspection. | Not required unless governance-relevant. | `EVIDENCE_LOG.md` |
| Traceability | Changed runtime docs link to relevant logs or runtime controls. | No traceability for governed change. | File inspection. | Required for block-level changes. | `AUDIT_TRAIL.md` |
| Evidence sufficiency | Required evidence is specific, current and verifiable. | Missing, ambiguous, stale or unsupported evidence. | `logs/EVIDENCE_LOG.md` entry. | Required when evidence supports decision. | `CERTIFICATION_LOG.md` |
| Audit sufficiency | Required audit links action, decision, evidence and rollback. | Missing required audit entry. | Audit log inspection. | `logs/AUDIT_TRAIL.md` entry. | `AUDIT_TRAIL.md` |
| Rollback | Rollback path is defined and inspectable. | No rollback path for medium+ or critical work. | Rollback section or certification entry. | Required for high/critical rollback posture. | `CERTIFICATION_LOG.md` |
| Compatibility | Compatibility impact is documented. | Breaking or uncertain compatibility without decision. | `runtime/compatibility-matrix.md` review. | Required when compatibility changes. | `GOVERNANCE_GATE_LOG.md` |
| Critical decisions | Critical decisions are identified and escalated. | Critical decision not logged. | Decision log entry. | Audit entry when applicable. | `DECISION_LOG.md`, `AUDIT_TRAIL.md` |
| Human authorization | Merge requires explicit Tiziano authorization for this PR. | Missing PR-specific authorization. | Decision or PR review reference. | Required before merge. | `DECISION_LOG.md` |

## Required commands before PR

```bash
git status
git branch --show-current
git diff --check
git diff --stat
```

Documentary validation tools may be executed only when they do not install
dependencies or alter the environment.

## Merge rule

Merge is always blocked until Tiziano explicitly authorizes the specific pull
request. Prior authorization for PR #5 does not apply to Block 8 or any future
pull request.
