# NEOS + NEXUS Operational Execution Control Map v0.1.0

## Purpose

This map consolidates connector readiness, authorization registry, execution boundary, batch governance, operational playbooks, human-adaptive output, and authorization enforcement into one quick control surface.

## Decision Flow

| Step | Control question | Decision |
| --- | --- | --- |
| 1 | Is the requested action inside an approved connector, account, environment, branch, file, PR, or object? | If no, stop or prepare a handoff only. |
| 2 | Is the action read, draft, write, submit, activate, merge, delete, notify, or schedule? | Classify before acting. |
| 3 | Does the action create live external effect, production change, permission change, communication, automation, spend, merge, or restricted data exposure? | If yes, require exact human authorization. |
| 4 | Is required authorization exact, current, and tied to this action? | If no, stop. |
| 5 | Is evidence available for scope, data class, validation, result, and rollback or irreversibility? | If no, escalate or block. |
| 6 | Can the action be completed within the requested output mode without hiding risk or authority limits? | If yes, execute or prepare within scope. |

## Execution Classes

| Class | Allowed movement |
| --- | --- |
| Execute | Perform only the exact approved action with evidence. |
| Prepare | Draft, validate, stage, or document without live effect. |
| Escalate | Pause for exact human approval or missing evidence. |
| Block | Refuse operational movement when prohibited or unsafe. |

## Compact Output Rule

Report only the operational result required by the user. Expand only for missing authorization, failed validation, or required stop evidence.
