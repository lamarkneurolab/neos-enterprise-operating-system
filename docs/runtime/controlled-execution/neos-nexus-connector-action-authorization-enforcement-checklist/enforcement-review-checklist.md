# Enforcement Review Checklist

## Purpose

This review checklist verifies that connector action enforcement was applied before execution, preparation, escalation, or block.

## Review Checklist

| Check | Pass condition |
| --- | --- |
| Requested action classified | Action type and criticality are named. |
| Authorization verified | Human approval is exact and current. |
| Scope matched | Approved scope equals requested scope. |
| Connector matched | Connector, account, environment, and tool are correct. |
| Data boundary checked | Data class is allowed and minimized. |
| External effect checked | Live effect is authorized or blocked. |
| Evidence preserved | Approval, validation, result, and rollback evidence are available. |
| PR safety checked | PR number and Head SHA are exact when merge authority is involved. |
| Stop condition applied | Missing evidence causes escalate or block, not execution. |

## Completion Standard

The action is enforceable only when the reviewer can reproduce the decision from compact evidence without assuming hidden authority.
