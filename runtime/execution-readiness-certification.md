# Execution Readiness Certification

Execution Readiness Certification determines whether a runtime execution flow
can be considered ready.

## Certification requirements

| Requirement | Approval condition | Blocking condition | Evidence | Audit | Rollback |
|---|---|---|---|---|---|
| Authorized input | Input has explicit authorization or permitted low-risk scope. | Missing authorization. | Authorization reference or user instruction. | Required for governance-relevant execution. | Stop execution. |
| Initial state | Initial state is declared and valid. | Unknown or invalid state. | State log or execution plan. | Required when state changes. | Restore previous valid state. |
| Task record | Task is identified or documented. | No task trace for governed work. | Task ID or documented task reference. | Required for medium+ work. | Block closure. |
| Event record | Event is planned or linked. | No event trace for runtime transition. | Event ID or planned event. | Required when event changes governance posture. | Mark event missing and record incident when needed. |
| State transition | Next state is valid. | State bypass or invalid transition. | State transition evidence. | Required for state change. | Revert or restore previous state. |
| Evidence plan | Evidence is planned before closure. | Missing evidence plan. | Expected evidence method. | Not required unless evidence supports decision. | Block closure. |
| Audit plan | Audit is planned for governed actions. | Missing audit plan for required audit. | Audit target and rationale. | Audit entry before closure. | Block merge. |
| Rollback plan | Rollback path is declared. | No rollback for medium+ or critical work. | Rollback section or command. | Required for high/critical rollback. | Close PR without merge if unresolved. |
| Risks | Risks are identified. | High or critical risk not recorded. | Risk notes or matrix row. | Required for critical risk. | Escalate decision. |
| Human-in-the-loop | Human approval point is defined. | Required human decision absent. | Decision or authorization reference. | Required before merge or critical action. | Stop action. |
| Closure criteria | Completion criteria are documented. | Closure criteria missing. | Checklist or validation plan. | Required for block-level closure. | Block closure. |

## Certification outcome

| Outcome | Meaning |
|---|---|
| `certified` | All required fields pass. |
| `certified_with_review` | Minor non-blocking gaps exist and are documented. |
| `blocked` | Required authorization, evidence, audit, rollback or state traceability is missing. |
| `rollback_required` | Execution cannot proceed safely without rollback or containment. |

## Log requirement

Record the outcome in `logs/CERTIFICATION_LOG.md`. Blocked outcomes that affect
closure or merge must also be reflected in `logs/GOVERNANCE_GATE_LOG.md` and
`logs/INCIDENT_LOG.md` when incident criteria are met.
