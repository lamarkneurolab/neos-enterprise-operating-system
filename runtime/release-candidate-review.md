# Release Candidate Review

Release Candidate Review determines whether a block can be considered a
candidate for closure.

It does not approve merge. Merge requires explicit Tiziano authorization for
the specific pull request.

## Required review fields

| Field | Requirement | Blocking condition | Log |
|---|---|---|---|
| Scope complete | Required block scope is implemented or justified. | Missing required scope without justification. | `RELEASE_CANDIDATE_REVIEW_LOG.md` |
| Files created | Expected new files exist or exception is documented. | Missing file without justification. | `RELEASE_CANDIDATE_REVIEW_LOG.md` |
| Files modified | Existing files changed only as needed for compatibility and links. | Unexplained incompatible edit. | `GOVERNANCE_GATE_LOG.md` |
| Markdown validation | Source remains Markdown and `git diff --check` passes. | Validation failure. | `EVIDENCE_LOG.md` |
| Traceability validation | Docs link to runtime controls and logs. | Missing traceability for governed change. | `CERTIFICATION_LOG.md` |
| Log validation | Decision, evidence, audit, state, incident and new logs are updated. | Required log missing. | `AUDIT_TRAIL.md` |
| Evidence validation | Evidence is sufficient and linked. | Missing or ambiguous evidence. | `EVIDENCE_LOG.md` |
| Audit validation | Audit is sufficient and linked. | Missing required audit. | `AUDIT_TRAIL.md` |
| Rollback validation | Rollback path exists. | No rollback for governed change. | `CERTIFICATION_LOG.md` |
| Restriction validation | No prohibited agents, permissions, secrets, dependencies, deletion, destructive changes or external activation. | Restriction violation. | `INCIDENT_LOG.md` |
| Residual risks | Remaining risks are documented. | High/critical residual risk unreviewed. | `GOVERNANCE_GATE_LOG.md` |
| ChatGPT recommendation | Reviewer recommendation is recorded. | Missing recommendation for RC posture. | `RELEASE_CANDIDATE_REVIEW_LOG.md` |
| Tiziano decision | Explicit decision is recorded. | Missing decision blocks approval and merge. | `DECISION_LOG.md` |

## Candidate outcomes

| Outcome | Meaning |
|---|---|
| `candidate_ready` | Scope and validation are complete; merge still requires Tiziano approval. |
| `candidate_with_notes` | Non-blocking risks remain and are documented. |
| `blocked` | Required scope, evidence, audit, rollback, logs or authorization are missing. |
| `not_candidate` | Scope is incomplete or restrictions are violated. |

## Block 8 release candidate posture

Block 8 may be recommended as `candidate_ready` only after:

- All expected Block 8 files exist.
- Required existing logs and compatibility documents are updated.
- `git diff --check` passes.
- Pull request is open against `main`.
- No merge has been executed.
- Tiziano has not been asked for merge authorization until review is complete.

## Block 9 validation linkage

Release candidate review is validated by
`runtime/release-readiness-validation.md`.

Release readiness validation must confirm required test cases, validation logs,
test evidence, audit, regression review, certification gates, governance gates,
blocking conditions and final recommendation before a block is considered ready
for human review.
