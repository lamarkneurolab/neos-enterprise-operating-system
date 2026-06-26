# Critical Decision Gates

Critical Decision Gates define changes that require escalation before closure,
merge or release candidate approval.

## Critical decisions

| Decision type | Critical trigger | Required evidence | Required audit | Required authorization | Rollback |
|---|---|---|---|---|---|
| Base architecture change | Execution-layer architecture changes or prior block relationship changes. | Architecture diff and compatibility review. | Required. | Tiziano approval when critical. | Restore prior architecture text. |
| External boundary change | External read/write/side effect boundary changes. | Boundary diff and risk classification. | Required. | Tiziano approval. | Restore prior boundary or close PR. |
| SDK contract change | Required field, compatibility, version or invocation rule changes. | SDK contract diff and compatibility matrix. | Required. | Tiziano approval for breaking change. | Restore or supersede contract. |
| Integration contract change | Entry, exit, failure, authorization, data or rollback rules change. | Integration contract diff. | Required. | Tiziano approval for external or breaking change. | Restore or supersede contract. |
| Runtime authorization change | Authorization gates or human approval semantics change. | Authorization diff and decision rationale. | Required. | Tiziano approval. | Restore prior authorization rule. |
| Memory/context change | Context reuse, persistence, resume or recovery criteria change. | Memory/context diff and risk review. | Required. | Tiziano approval for high/critical reuse. | Revoke context or restore prior rule. |
| Evidence/audit change | Evidence or audit sufficiency requirements are weakened or expanded. | Rule diff and governance rationale. | Required. | Tiziano approval for weakening or critical expansion. | Restore prior sufficiency rule. |
| Compatibility change | Compatibility between blocks, modules or contracts changes. | Compatibility matrix diff. | Required. | Tiziano approval for breaking compatibility. | Restore previous compatible state. |
| Rollback impact | Rollback becomes harder, unavailable or critical. | Rollback readiness record. | Required. | Tiziano approval for critical rollback. | Close PR or restore rollback path. |
| External execution enablement | Real external execution becomes possible. | Boundary evidence and exact action proposal. | Required. | Tiziano approval for exact action. | Stop and keep blocked until approved. |

## Decision log rule

Critical decisions must be recorded in `logs/DECISION_LOG.md` before merge or
release candidate approval. If a critical decision is identified after review,
the PR remains open until the decision, evidence, audit and rollback posture are
complete.
