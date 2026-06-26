# Evidence Sufficiency Rules

Evidence is sufficient only when it is specific, current, verifiable and linked
to the action it supports.

## Minimum evidence

Minimum evidence can include:

- `git status` output.
- `git branch --show-current` output.
- `git diff --check` output.
- `git diff --stat` output.
- File inspection results.
- Commit SHA.
- Push output.
- Pull request URL.
- Validation command output.
- Explicit human authorization reference.
- Compatibility matrix inspection.
- Log entries for decision, audit, state, incident or certification.

## Insufficient evidence

Evidence is insufficient when it is:

- Missing.
- Ambiguous.
- Stale.
- Fabricated.
- Unsupported by command output or file inspection.
- Not linked to the governed action.
- Not reproducible or independently inspectable.
- Only a claim of completion without proof.

## Blocking rules

| Missing evidence type | Blocks closure | Blocks merge | Requires human review |
|---|---:|---:|---:|
| Required validation evidence | Yes | Yes | Yes |
| Required authorization evidence | Yes | Yes | Yes |
| Required rollback evidence | Yes | Yes | Yes for high/critical |
| Required compatibility evidence | Yes | Yes when compatibility changes | Yes for breaking change |
| Required audit-support evidence | Yes | Yes when audit is required | Yes |
| Required incident evidence | Yes until contained | Yes for open high/critical incident | Yes |

## Evidence log linkage

Required evidence belongs in `logs/EVIDENCE_LOG.md`.

Each evidence entry should include:

- Date.
- Evidence ID.
- Action.
- Result.
- Verification method.

Block 8 uses `EVD-NEOS-F3-009` for the documentary baseline of Runtime
Certification & Governance Gates v0.1.0.

## Fabrication prevention

Evidence must not be invented from intention or plan. If a command, file,
commit, push or PR has not happened, the evidence must state that it is pending,
blocked or not applicable.

## Block 9 validation linkage

Evidence sufficiency can be validated through `runtime/evidence-validation.md`
and `logs/TEST_EVIDENCE_LOG.md`.

Test evidence must be specific, current, verifiable, linked to the test case or
scenario, and linked to audit when audit is required.
