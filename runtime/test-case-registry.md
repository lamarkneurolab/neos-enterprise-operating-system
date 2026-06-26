# Test Case Registry

## Purpose

Define the documentary registry for NEOS runtime validation test cases.

## Scope

The registry records test cases for authorization, execution, coordination,
observability, audit, memory, SDK, integration, certification, governance,
rollback, failure, evidence, audit sufficiency, regression and release
readiness.

## Related runtime components

All Block 3-8 runtime components and Block 9 validation documents.

## Validation model

| Field | Requirement |
|---|---|
| Test Case ID | Stable ID such as `TC-NEOS-F3-009-001`. |
| Title | Short title. |
| Runtime area | Area under validation. |
| Risk level | `low`, `medium`, `high` or `critical`. |
| Owner | Reviewer or governance role. |
| Status | `draft`, `ready`, `passed`, `failed`, `blocked`, `deprecated`. |
| Related component | Runtime document or module. |
| Related contract | SDK, integration or runtime contract when applicable. |
| Related certification gate | Certification gate reference. |
| Related governance gate | Governance matrix or gate reference. |
| Evidence link | Evidence or test evidence reference. |
| Audit link | Audit trail reference. |
| Rollback requirement | Rollback or containment requirement. |
| Last review date | Date of latest review. |

## Required evidence

Test case record, related scenario, validation result and evidence reference in
`logs/TEST_EVIDENCE_LOG.md` or `logs/EVIDENCE_LOG.md`.

## Required audit trail

Audit is required for high, critical, release-readiness, merge-readiness,
rollback or governance-gate test cases.

## Pass criteria

The test case is complete, linked, evidenced, audited when required and has no
blocking regression.

## Fail criteria

The test case fails expected behavior, lacks required evidence or cannot be
audited when audit is required.

## Blocking conditions

Missing required test case, failed high/critical test case, missing evidence,
missing audit or unresolved rollback posture blocks release readiness.

## Rollback considerations

Rollback is to restore prior test case status, mark the case deprecated, revert
the documentation commit or close the PR without merge.

## Human authorization requirements

Human authorization is required for merge readiness, release readiness,
critical rollback or any test that would otherwise imply real external action.

## Related certification/governance gates

Release Candidate Readiness, Evidence Sufficiency, Audit Sufficiency, Rollback
Readiness and Human Authorization Requirement.

## Minimum checklist

- [ ] Test Case ID exists.
- [ ] Scenario linked.
- [ ] Risk level assigned.
- [ ] Evidence linked.
- [ ] Audit linked when required.
- [ ] Rollback declared.
- [ ] Gates linked.
