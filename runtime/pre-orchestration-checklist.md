# Pre-Orchestration Checklist

## Purpose

Define the minimum checklist required before a future runtime capability can
enter orchestration readiness review.

## Checklist

- [ ] Source branch verified.
- [ ] Scope validated.
- [ ] Risk classified.
- [ ] Applicable validations identified.
- [ ] Evidence plan defined.
- [ ] Audit trail defined.
- [ ] Rollback plan defined.
- [ ] Human authorization requirement defined.
- [ ] Impact on permissions evaluated.
- [ ] Impact on secrets evaluated.
- [ ] Impact on dependencies evaluated.
- [ ] Confirmation that no business agents are created.
- [ ] Confirmation that no commercial, clinical, documentation, marketing,
      sales or operations agents are created.
- [ ] Confirmation that no productive execution is activated.
- [ ] Confirmation that no external integration is activated.
- [ ] Governance gate posture reviewed.
- [ ] Certification gate posture reviewed.

## Blocking rule

Any unchecked required item blocks progression beyond
`readiness_review_required`.

## Relationship with preflight checks

This checklist feeds Block 11 preflight checks. Passing this checklist does not
start execution or activation; it only supports dry-run simulation review.
