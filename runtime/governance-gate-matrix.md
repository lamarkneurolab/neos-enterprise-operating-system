# Governance Gate Matrix

The Governance Gate Matrix maps runtime change types to required certification
and governance controls.

## Matrix

| Change type | Risk level | Required gate | Evidence required | Audit required | Human authorization required | Rollback required | Logs to update | Allowed result |
|---|---|---|---|---|---|---|---|---|
| Runtime documentation | Low/medium | Evidence Sufficiency, Audit Sufficiency when governance-relevant | File inspection, `git diff --check`, changed file list | Required for block-level or governance-relevant documentation | Required for merge | Revert commit or close PR | `EVIDENCE_LOG.md`, `AUDIT_TRAIL.md`, `EXECUTION_STATE_LOG.md` | Close only after validation and PR review |
| SDK contracts | Medium/high | SDK Contract Compliance, Evidence Sufficiency, Audit Sufficiency, Critical Decision when breaking | Contract diff, compatibility check | Required | Required for merge and breaking change approval | Restore prior contract or supersede version | `SDK_CONTRACT_LOG.md`, `GOVERNANCE_GATE_LOG.md`, `DECISION_LOG.md` | Integrate only if compatible or explicitly approved |
| Integration contracts | Medium/high | Integration Readiness, Integration Contract Compliance, Human Authorization if external | Contract diff, boundary check | Required | Required for merge; required before any external action | Revert, supersede or close PR | `INTEGRATION_CONTRACT_LOG.md`, `GOVERNANCE_GATE_LOG.md`, `INCIDENT_LOG.md` if blocked | Integrate only as documentation; no live activation |
| Internal interfaces | Medium | Evidence Sufficiency, SDK Contract Compliance when SDK-facing | Interface matrix inspection | Required when runtime boundary changes | Required for merge | Restore prior interface language | `GOVERNANCE_GATE_LOG.md`, `EVIDENCE_LOG.md` | Merge only after compatibility review |
| Extension rules | Medium/high | Critical Decision if rules expand capabilities | Rule diff and risk classification | Required | Required for merge; Tiziano approval if critical | Restore prior rules | `DECISION_LOG.md`, `AUDIT_TRAIL.md`, `GOVERNANCE_GATE_LOG.md` | Promote only when boundaries remain safe |
| External execution boundaries | High/critical | Human Authorization, Critical Decision, Integration Readiness | Boundary diff and prohibited action review | Required | Required before any external read/write/side effect | Stop action, revert or close PR | `DECISION_LOG.md`, `AUDIT_TRAIL.md`, `INCIDENT_LOG.md` if violated | Default result is blocked unless explicitly authorized |
| Memory and context persistence | Medium/high | Memory Safety, Evidence Sufficiency, Audit Sufficiency | Context validity evidence and snapshot reference | Required when context affects execution or recovery | Required for high/critical reuse or critical recovery | Revoke context or block resume | `MEMORY_LOG.md`, `CONTEXT_SNAPSHOT_LOG.md`, `CERTIFICATION_LOG.md` | Reuse only if current, valid and audited |
| Observability and audit | Medium/high | Audit Sufficiency, Evidence Sufficiency | Audit trail diff and evidence linkage | Required | Required for merge | Restore prior audit rule or add missing audit | `AUDIT_TRAIL.md`, `GOVERNANCE_GATE_LOG.md` | Close only when audit trail is complete |
| Task Queue, Event Bus and State Manager | Medium/high | Execution Readiness, Audit Sufficiency, Critical Decision when state semantics change | Task/event/state traceability | Required | Required for merge and critical state changes | Restore prior transition rule | `EXECUTION_STATE_LOG.md`, `AUDIT_TRAIL.md`, `INCIDENT_LOG.md` | Promote only if valid transitions are preserved |
| Release candidate | High | Release Candidate Readiness, Human Authorization, Evidence Sufficiency, Audit Sufficiency | RC review entry, validation outputs, risk notes | Required | Tiziano decision required | Keep PR open or close without merge | `RELEASE_CANDIDATE_REVIEW_LOG.md`, `CERTIFICATION_LOG.md`, `DECISION_LOG.md` | Candidate only after complete review |
| Rollback | Medium/high/critical | Rollback Readiness, Human Authorization for critical rollback | Rollback condition, scope and verification method | Required for high/critical rollback | Required for critical rollback execution | Required by definition | `CERTIFICATION_LOG.md`, `GOVERNANCE_GATE_LOG.md`, `INCIDENT_LOG.md` | Execute only when authorized and documented |
| Incident | Medium/high/critical | Evidence Sufficiency, Audit Sufficiency, Rollback Readiness when needed | Incident facts and containment evidence | Required for governance-relevant incidents | Required for critical remediation | Containment or rollback path | `INCIDENT_LOG.md`, `AUDIT_TRAIL.md`, `EVIDENCE_LOG.md` | Close only after containment and evidence |
| Compatibility | Medium/high | SDK Contract Compliance, Integration Contract Compliance, Critical Decision when breaking | Compatibility matrix diff | Required | Required for merge; Tiziano approval if breaking | Restore previous compatible state | `GOVERNANCE_GATE_LOG.md`, `DECISION_LOG.md`, `SDK_CONTRACT_LOG.md` | Compatible, compatible-with-review or blocked |

## Global blocking conditions

The governed outcome is blocked when any required item is missing:

- Evidence.
- Audit.
- Human authorization.
- Rollback path.
- Compatibility review.
- Incident containment.
- Critical decision record.

Blocked outcomes must be recorded in `logs/GOVERNANCE_GATE_LOG.md` and, when
they affect closure or merge, in `logs/INCIDENT_LOG.md`.

## Block 9 validation linkage

Governance gate outcomes are validated by
`runtime/governance-gate-validation.md`. Change types that affect release
readiness should also link `runtime/regression-validation.md` and
`runtime/release-readiness-validation.md`.
