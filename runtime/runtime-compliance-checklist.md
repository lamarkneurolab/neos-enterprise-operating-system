# Runtime Compliance Checklist

This checklist applies before closing any NEOS Fase 3 block or pull request
related to the execution layer.

## Checklist

- [ ] Architecture remains compatible with Blocks 1-7.
- [ ] GitHub remains the canonical source.
- [ ] Markdown `.md` remains the official source format.
- [ ] No business agents are created.
- [ ] No commercial, clinical, documentation, marketing, sales or operations agents are created.
- [ ] No permissions are changed.
- [ ] No secrets are managed.
- [ ] No dependencies are installed without explicit authorization.
- [ ] No files are deleted without explicit authorization.
- [ ] No destructive changes are executed.
- [ ] No external integrations are activated.
- [ ] Authorization Flow is respected.
- [ ] Execution Flow has task, event and state traceability.
- [ ] Task Queue, Event Bus and State Manager links are preserved when applicable.
- [ ] Observability requirements are documented.
- [ ] Audit Trail requirements are documented.
- [ ] Runtime Memory and Context Persistence constraints are respected.
- [ ] SDK Contracts remain compatible with Block 7.
- [ ] Integration Contracts remain compatible with Block 7.
- [ ] External Execution Boundaries block real side effects by default.
- [ ] Evidence is sufficient under `runtime/evidence-sufficiency-rules.md`.
- [ ] Audit is sufficient under `runtime/audit-sufficiency-rules.md`.
- [ ] Rollback readiness is documented.
- [ ] Human authorization gates are identified.
- [ ] Critical decision gates are identified.
- [ ] Release candidate review is complete when closing a block.
- [ ] Required logs are updated.
- [ ] `git diff --check` passes.
- [ ] Pull request is open for review.
- [ ] Pull request is not merged automatically.

## Closure rule

If any required checklist item fails, closure is blocked. The allowed next step
is remediation, incident registration, rollback readiness review, PR closure
without merge or explicit human authorization when the action is allowed only by
Tiziano.
