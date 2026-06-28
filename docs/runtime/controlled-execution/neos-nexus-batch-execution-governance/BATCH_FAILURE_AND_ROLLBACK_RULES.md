# Batch Failure and Rollback Rules

## Failure triggers

A batch stops for the affected block when route validation fails, file count differs, a deletion appears, a branch contains extra commits, a commit changes files outside route, a PR targets the wrong base, or a request attempts merge, auto-merge, production activation, sensitive data handling, or external live effects.

## Partial batch continuation

Unaffected blocks may continue only when their branches, paths, commits, and PRs remain independent. A shared failure stops the whole batch when it affects common scope, authorization, base branch, or repository integrity.

## Rollback posture

Rollback is local and documentation-first unless separately authorized. Before PR creation, rollback may mean abandoning the branch or amending the single commit. After PR creation, rollback may mean closing the PR or preparing a corrective commit according to reviewer direction.

## No destructive recovery by default

Destructive reset, force push, deletion, branch removal, or PR closure requires explicit authorization unless it is the only safe way to stop an unsubmitted local prepare action and no user work is affected.

## Failure handoff

The handoff records block number, branch, commit if present, failed check, changed paths, deletion status, PR status, and recommended correction. It must not include secrets or restricted data.

## Re-entry

A failed block may re-enter the batch only after the blocker is corrected and the block again satisfies route, file count, deletion, branch, commit, PR, and merge-boundary rules.
