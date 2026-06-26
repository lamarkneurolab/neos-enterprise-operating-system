# Integration Readiness Certification

Integration Readiness Certification determines whether a future integration,
integration contract or external boundary can be considered ready.

This certification does not activate real integrations.

## Certification requirements

| Requirement | Approval condition | Blocking condition | Evidence | Audit | Rollback |
|---|---|---|---|---|---|
| Integration contract | Contract exists and declares required fields. | Missing contract or incomplete required fields. | Contract inspection. | Required for contract change. | Supersede or restore prior contract. |
| External boundary | Boundary is documented and respected. | Real external execution or boundary ambiguity. | Boundary review. | Required for boundary changes. | Stop action; revert or close PR. |
| Allowed data | Allowed data is identified. | Data category undefined. | Contract data section. | Required for high-risk data posture. | Block integration readiness. |
| Prohibited data | Prohibited data is identified. | Prohibited data can cross boundary. | Contract data section. | Required if violation occurs. | Revoke context and record incident. |
| Block 7 compatibility | SDK and integration contracts remain compatible. | Contradiction with Block 7. | Compatibility matrix review. | Required for compatibility change. | Restore Block 7-compatible text. |
| Evidence minimum | Evidence is specific and verifiable. | Missing or ambiguous evidence. | `EVIDENCE_LOG.md` entry. | Required when evidence supports decision. | Block closure. |
| Audit minimum | Audit links action, decision and rollback. | Missing required audit. | Audit trail inspection. | `AUDIT_TRAIL.md` entry. | Block merge. |
| Integration rollback | Rollback or containment path exists. | No rollback for integration failure. | Rollback section. | Required for high/critical rollback posture. | Close PR or revert. |
| Human authorization | Required approval point is identified. | Missing approval for merge or external action. | Decision reference. | Required before merge or external action. | Stop action. |
| External execution prohibition | Real external execution remains blocked by default. | Live connector, service, workflow or side effect activated. | Diff and command inspection. | Required if attempted. | Stop, record incident and rollback only with approval. |

## Certification outcome

Integration readiness may be marked `certified` only when the contract is
documentary, boundary-safe, evidenced, audited and rollback-ready.

Any requested real external action remains blocked until separately and
explicitly authorized by Tiziano for the exact action.

## Block 9 validation linkage

Integration readiness can be validated through
`runtime/integration-contract-validation.md` and
`runtime/runtime-contract-validation.md`.

Validation must confirm that external execution remains blocked by default,
evidence and audit are sufficient, rollback is defined and no live integration
is activated.
