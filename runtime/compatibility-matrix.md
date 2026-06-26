# Compatibility Matrix

This matrix records compatibility between Block 7 Runtime SDK & Integration
Contracts and NEOS Fase 3 Blocks 1-6.

## Module compatibility

| Block or module | Contract dependency | Compatibility | Required control |
|---|---|---|---|
| Block 1 - Repository Initialization | Markdown source and GitHub canonical source. | Compatible | Keep all source files as `.md`. |
| Block 2 - Registry System | Capability, permission, tool, connector and runtime registry references. | Compatible with review | Do not modify permissions or registry semantics in Block 7. |
| Block 3 - Authorization Flow | Authorization gates before execution, push, PR, external or destructive work. | Compatible | No SDK invocation without authorization. |
| Block 4 - Task Queue | Task records for SDK and integration work. | Compatible | Link `task_id` and rollback requirement. |
| Block 4 - Event Bus | Lifecycle events for contract and invocation actions. | Additive | New event names are documentary only. |
| Block 4 - State Manager | Valid state transitions and rollback states. | Compatible | Do not skip authorization, evidence or rollback states. |
| Block 5 - Observability | Runtime inspection of SDK and integration actions. | Compatible | Medium+ events link evidence. |
| Block 5 - Audit Trail | Governance audit for contract changes and boundary changes. | Compatible | Audit major, high-risk and external-boundary changes. |
| Block 5 - Incident Records | Failure, missing evidence, missing audit and boundary incidents. | Compatible | Block closure when required incidents remain open. |
| Block 6 - Runtime Memory | Valid context only after review. | Compatible | No stale, revoked or prohibited memory reuse. |
| Block 6 - Context Persistence | Context references with evidence and audit. | Compatible | Persist references, not secrets or unsupported claims. |
| Block 7 - SDK Contracts | Runtime SDK baseline. | Baseline | Use v0.1.0 contract template. |
| Block 7 - Integration Contracts | Integration entry, exit, failure and rollback rules. | Baseline | External execution blocked by default. |
| Block 8 - Certification Gates | Runtime certification baseline. | Additive | Required gates must pass before closure, promotion, release candidate review or merge. |
| Block 8 - Governance Gates | Cross-cutting governance matrix, pre-merge review and human authorization gates. | Additive | Missing evidence, audit, rollback, compatibility or human authorization blocks closure and merge. |

## Contract compatibility

| Contract | Version | Compatible modules | Compatibility status | Evidence |
|---|---|---|---|---|
| SDK Runtime Contract | `0.1.0` | Authorization, Task Queue, Event Bus, State Manager, Observability, Audit Trail | `compatible` | `EVD-NEOS-F3-008` |
| SDK Consumer Contract | `0.1.0` | Authorization, Registry System, SDK Runtime | `compatible` | `EVD-NEOS-F3-008` |
| SDK Provider Contract | `0.1.0` | Registry System, SDK Runtime, Compatibility Matrix | `compatible_with_review` | `EVD-NEOS-F3-008` |
| SDK Invocation Contract | `0.1.0` | Authorization, Task Queue, Event Bus, State Manager | `compatible` | `EVD-NEOS-F3-008` |
| SDK Response Contract | `0.1.0` | State Manager, Evidence Log, Audit Trail | `compatible` | `EVD-NEOS-F3-008` |
| SDK Error Contract | `0.1.0` | Observability, Audit Trail, Incident Log, Rollback | `compatible` | `EVD-NEOS-F3-008` |
| SDK Evidence Contract | `0.1.0` | Evidence Log, Audit Trail | `compatible` | `EVD-NEOS-F3-008` |
| SDK Audit Contract | `0.1.0` | Audit Trail, Decision Log, Evidence Log | `compatible` | `EVD-NEOS-F3-008` |
| SDK Version Contract | `0.1.0` | Compatibility Matrix, SDK Contract Log | `compatible` | `EVD-NEOS-F3-008` |
| Integration Contract | `0.1.0` | Authorization, Task Queue, Event Bus, State Manager, Observability | `compatible` | `EVD-NEOS-F3-008` |
| External Execution Boundaries | `0.1.0` | Authorization, Registry System, Incident Records, Rollback | `compatible` | `EVD-NEOS-F3-008` |
| Certification Gates | `0.1.0` | Authorization, Execution Flow, Task Queue, Event Bus, State Manager, Observability, Audit Trail, Runtime Memory, SDK Contracts, Integration Contracts | `compatible` | `EVD-NEOS-F3-009` |
| Governance Gate Matrix | `0.1.0` | Blocks 1-7, Evidence Log, Audit Trail, Decision Log, Incident Log, Release Candidate Review | `compatible` | `EVD-NEOS-F3-009` |
| Human Authorization Gates | `0.1.0` | Authorization Flow, Pre-merge Governance Review, Release Candidate Review | `compatible` | `EVD-NEOS-F3-009` |

## Risk matrix

| Risk ID | Risk | Likelihood | Impact | Control | Rollback |
|---|---|---|---|---|---|
| R-SDK-001 | SDK contract used without authorization. | Medium | High | Authorization Flow gate. | Block invocation and record incident. |
| R-SDK-002 | Contract version drift. | Medium | Medium | Version log and compatibility matrix. | Restore prior version. |
| R-SDK-003 | Missing evidence. | Medium | High | SDK Evidence Contract. | Block closure; record incident. |
| R-SDK-004 | Missing audit. | Medium | High | SDK Audit Contract. | Record missing audit incident. |
| R-INT-001 | External execution attempted. | Low | High | External Execution Boundaries. | Stop execution; close PR or revert. |
| R-INT-002 | Prohibited data crosses interface. | Low | Critical | Internal Interface data rules. | Revoke context and record incident. |
| R-MEM-001 | Stale context reused. | Medium | High | Runtime Memory review. | Mark stale or revoked. |
| R-VER-001 | Breaking change merged as minor. | Low | High | Versioning review. | Revert commit or supersede version. |
| R-GOV-001 | Required certification gate is bypassed. | Medium | High | Block 8 Certification Gates. | Block closure, remediate or close PR without merge. |
| R-GOV-002 | Merge proceeds without PR-specific Tiziano authorization. | Low | Critical | Human Authorization Gates and Pre-merge Governance Review. | Stop merge; revert if merged without authorization. |
| R-GOV-003 | Release candidate is declared with incomplete evidence or audit. | Medium | High | Release Candidate Review and sufficiency rules. | Keep PR open until gaps are remediated. |

## Review checklist

- [ ] All contract changes are Markdown.
- [ ] No dependencies are added.
- [ ] No permissions are changed.
- [ ] No secrets are managed.
- [ ] No external execution is performed.
- [ ] No business agents are created.
- [ ] Compatibility with Blocks 1-6 is preserved.
- [ ] SDK contracts include required fields.
- [ ] Integration contracts include required fields.
- [ ] Internal interfaces include required fields.
- [ ] Evidence, audit, state and incident logs are updated when applicable.
- [ ] Rollback path is documented.
- [ ] Required Block 8 certification and governance gates pass.
- [ ] Human authorization is identified and merge remains blocked until PR-specific Tiziano approval.

## Certification checklist

- [ ] `git diff --check` passes.
- [ ] File inspection confirms required Block 7 files exist.
- [ ] Logs include Block 7 decision, evidence, audit and state entries.
- [ ] Incident log records no incident or any discovered incident.
- [ ] Branch is not `main`.
- [ ] PR is opened for review.
- [ ] PR is not merged automatically.
- [ ] Block 8 release candidate review is complete when a block is declared candidate-ready.
