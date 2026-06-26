# Activation Decision Matrix

## Purpose

Define allowed activation decisions.

## Decisions

| Decision | Meaning |
|---|---|
| `approve-for-future-execution` | Request is approved for a separately authorized future execution window. |
| `deny` | Request is rejected. |
| `defer` | Request is postponed pending remediation. |
| `block` | Request cannot proceed due to blocker. |
| `abort` | Request is stopped due to abort condition. |
| `request-more-evidence` | Evidence package is insufficient. |
| `request-risk-review` | Risk acceptance requires review. |
| `request-human-approval` | Explicit human approval is required. |

## Rule

No decision executes anything by itself. Even approval requires the exact
future execution scope and post-authorization controls to remain valid.

## Block 13 transition

`approve-for-future-execution` means the request may be reviewed under
`runtime/controlled-execution-activation-protocol.md`; it is not a go decision.
