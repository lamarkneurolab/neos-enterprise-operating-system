# NEOS Runtime Authorization & Execution Flow v0.1.0

This document is the operational entry point for NEOS Block 3: Runtime
Authorization & Execution Flow.

Block 3 defines how an incoming task becomes an authorized, tool-backed,
verifiable and auditable execution. It does not create business agents, change
permissions or merge work automatically.

## Canonical documents

| Document | Purpose |
|---|---|
| `docs/execution-layer/runtime-authorization-execution-flow-v0.1.0.md` | Canonical Block 3 specification. |
| `docs/execution-layer/authorization-flow.md` | Authorization rules and decision gates. |
| `docs/execution-layer/execution-engine.md` | Execution engine stages, state machine and failure handling. |
| `logs/DECISION_LOG.md` | Governance decision record. |
| `logs/EVIDENCE_LOG.md` | Evidence record for completed implementation work. |

## Execution promise

NEOS may execute only when all of the following are true:

1. The task intent is classified.
2. Required registries are consulted.
3. Risk is assessed.
4. Required human authorization is present.
5. A concrete execution plan exists.
6. Execution uses real tools available in the current runtime.
7. Results are verified.
8. Evidence and audit records are produced.
9. A rollback path is known or the absence of rollback is explicitly recorded.

## Non-goals

- No business agents are created by this block.
- No permissions are modified by this block.
- No automatic merge is performed by this block.
- No empty pull request should be opened.

## Minimal lifecycle

```text
intake
  -> intent_classification
  -> registry_consultation
  -> risk_classification
  -> authorization_gate
  -> execution_plan
  -> tool_execution
  -> verification
  -> evidence_logging
  -> audit_recording
  -> closed
```

If any gate fails, execution moves to `blocked`, `failed` or `rollback_required`
according to the rules in the canonical specification.
