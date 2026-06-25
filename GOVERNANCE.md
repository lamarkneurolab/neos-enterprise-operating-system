# NEOS Governance

## Source of truth hierarchy

1. GitHub repository
2. Markdown source files
3. Google Drive mirror
4. ChatGPT orchestration decisions
5. Codex engineering execution

## Required controls

Every structural or executable change must include:

- authorization status;
- execution actor;
- affected files;
- evidence;
- audit log;
- rollback path;
- verification method.

## Authorization model

Actions are classified as:

- Low risk: documentation-only changes without operational effect.
- Medium risk: repository structure, registry, configuration or governance updates.
- High risk: execution, permissions, credentials, deletion, production workflows or automation.

Medium and high-risk actions require explicit human authorization before execution.
