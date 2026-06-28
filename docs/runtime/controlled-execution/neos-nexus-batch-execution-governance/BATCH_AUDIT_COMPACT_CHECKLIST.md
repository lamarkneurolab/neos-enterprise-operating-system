# Batch Audit Compact Checklist

## Per-block checklist

| Check | Requirement |
| --- | --- |
| Route | The block path matches the requested route exactly. |
| File count | The path contains the exact requested Markdown file count. |
| Change boundary | The commit changes only the block route. |
| Deletions | The commit contains zero deletions unless explicitly authorized. |
| Commit count | The branch contains one block commit beyond main. |
| PR target | The PR targets main. |
| Production boundary | No production live action is included. |
| Sensitive boundary | No secrets, real credentials, or C4-C7 data are included. |
| External effects | No Drive, communication, campaign, automation, CI, or runner effect is triggered unless separately authorized. |
| Merge status | No merge or auto-merge is performed. |

## Batch checklist

The batch record confirms that every block has its own branch, commit, PR, validation record, and remaining merge authorization requirement. Shared batch status cannot replace per-block evidence.

## Evidence format

Evidence should be compact and reproducible: command names, path counts, changed-file summaries, and deletion checks. Evidence must avoid secrets, credentials, and unnecessary external payloads.

## Failure notation

A failed checklist item records the block, failed condition, stop decision, and required human authorization or correction path.

## Review readiness

A batch is review-ready only when all included blocks pass their per-block checklists or are explicitly marked stopped with a handoff.
