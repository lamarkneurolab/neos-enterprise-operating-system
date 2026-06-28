# GitHub Connector Playbook

## Allowed preparation

GitHub preparation may create local branches, local commits, PR descriptions, review packets, release notes, evidence checklists, and merge authorization templates when no merge, auto-merge, CI runner, or production deployment is triggered.

## Execute boundary

GitHub execution requires exact repository, base branch, head branch, action type, and authorization. Creating a PR is permitted only when the branch contents are bounded, the PR target is named, and the action does not imply merge authority.

## Required checks

Before a GitHub action, confirm that the worktree is clean or that unrelated changes are not touched, the branch matches one block of work, the commit includes only the intended path, and no deletion appears outside scope.

## Escalation triggers

Escalate when repository identity is uncertain, base branch differs from the request, branch naming conflicts, PR body requirements are missing, status checks require live CI, or the user requests a merge without the exact PR number and exact Head SHA.

## Block conditions

Block destructive reset, force push without explicit authorization, merge, auto-merge, production deployment, secret exposure, dependency installation, CI runner activation, and edits outside the approved route.

## Handoff evidence

The GitHub handoff records branch name, commit title, changed paths, deletion count, PR target, validation commands, and any merge authorization still required.
