# State Recovery Rules

State Recovery Rules define how NEOS may recover a prior operational state
using persisted context and execution snapshots.

The v0.1.0 recovery layer is documentary. It defines review criteria and does
not perform automated rollback or state mutation.

## Purpose

State Recovery protects NEOS from restoring unaudited, unauthorized or
incident-conflicted states.

## Recoverable state classes

| State class | Recovery rule |
|---|---|
| `last_stable_state` | Recover only when evidence and state log agree. |
| `last_audited_state` | Recover only when audit linkage is complete. |
| `last_authorized_state` | Recover only when authorization remains applicable. |
| `last_reliable_snapshot` | Recover only when snapshot validation is current. |
| `pre_incident_state` | Recover only after incident review and containment. |
| `pre_rollback_state` | Use for analysis unless reversal is explicitly authorized. |
| `post_rollback_state` | Recover as current only when rollback evidence is complete. |
| `non_recoverable_state` | Do not recover when evidence, audit or incident status blocks trust. |

## Minimum recovery criterion

```text
A state may be recovered only when it has sufficient evidence, linked audit
and no critical conflict with open incidents.
```

## Required recovery checks

| Check | Requirement |
|---|---|
| State identity | `state_id` exists and links to a task. |
| Snapshot identity | `snapshot_id` exists when recovery uses a snapshot. |
| Evidence linkage | Evidence log confirms the state or rollback path. |
| Audit linkage | Audit trail confirms governance-relevant recovery facts. |
| Incident status | Open incidents do not conflict with recovery. |
| Authorization | Recovery is allowed by current authorization. |
| Rollback linkage | Rollback references exist when recovery follows rollback. |
| Memory boundary | Prohibited memory is excluded. |

## Recovery decision values

| Decision | Meaning |
|---|---|
| `recoverable` | State may be used after evidence, audit and authorization review. |
| `not_recoverable` | State must not be used. |
| `review_required` | Human review is required. |
| `blocked_incident` | Open incident blocks recovery. |
| `blocked_evidence` | Required evidence is missing. |
| `blocked_audit` | Required audit linkage is missing. |
| `blocked_authorization` | Required authorization is missing. |

## Rules

- Recovery must not skip the State Manager transition rules.
- Recovery must not treat a snapshot as current truth without validation.
- Recovery after rollback must preserve rollback evidence.
- Recovery involving high or critical memory requires explicit review.
- Non-recoverable states must be preserved as history only when retention rules
  allow it.

## Non-goals

- No automated rollback engine is introduced.
- No production state machine service is introduced.
- No database persistence is introduced.
