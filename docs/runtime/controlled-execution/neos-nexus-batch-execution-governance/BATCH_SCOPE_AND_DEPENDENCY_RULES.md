# Batch Scope and Dependency Rules

## Scope boundary

Batch scope is limited to the named blocks, named routes, named files, and documentation-only changes. No block may modify another block route unless that modification is explicitly listed in its own objective.

## Path isolation

Each block path is validated independently. A block fails validation if it changes files outside its route, deletes existing material outside its route, or introduces shared state that makes the PR dependent on an unapproved change.

## Dependency classification

| Dependency type | Handling |
| --- | --- |
| None | PR may be reviewed independently. |
| Informational | PR may mention related work without requiring it. |
| Review-order | PR should be reviewed after another PR but remains merge-blocked until dependency is approved. |
| Merge-order | PR must not merge until the named upstream PR is merged and the Head SHA is revalidated. |

## Documentation dependency

References to other blocks are allowed when they are conceptual and do not require merged files to render the current documentation meaningful.

## Conflict handling

If two blocks need the same file, the batch must stop and split the shared edit into a separately authorized block or establish an explicit dependency plan.

## Scope drift

Any discovered need to change governance, registry, root README, version, changelog, or shared index files requires escalation unless the batch request explicitly included those files.
