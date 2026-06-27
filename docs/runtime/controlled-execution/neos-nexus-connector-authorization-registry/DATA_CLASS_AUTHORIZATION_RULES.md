# Data Class Authorization Rules v0.1.0

## Purpose

These rules classify data from C0 to C7 and define when NEOS/NEXUS may read, prepare, modify, transfer, expose, or use data operationally. The rules apply to connectors, tools, documents, runtime agents, automations, repositories, and external systems.

This block does not authorize use of real sensitive data in classes C4-C7.

## Data Classes

| Class | Name | Examples | Default Authorization |
| --- | --- | --- | --- |
| C0 | Public or intentionally published data | Public documentation, public website copy, public repository metadata | Permitted when within approved scope. |
| C1 | Internal non-sensitive operational data | Internal process notes, non-sensitive planning docs, low-risk technical metadata | Permitted when within approved scope. |
| C2 | Controlled internal project data | Non-public roadmaps, architecture docs, repository implementation details, internal governance records | Permitted only within approved project, repository, branch, and path scope. |
| C3 | Confidential business or technical data | Private strategy, unreleased capabilities, non-public partner context, controlled execution maps | Permitted only with clear scope, evidence, and need-to-use. |
| C4 | Restricted personal or account-linked data | Personal identifiers, private contact information, account-specific usage records, mailbox or calendar content | Requires explicit human authorization before access, modification, transfer, exposure, or operational use. |
| C5 | Highly sensitive business, financial, legal, or credential-adjacent data | Contracts, invoices, pricing approvals, billing data, secrets metadata, access tokens metadata, security-sensitive operational details | Requires explicit human authorization and critical evidence controls. |
| C6 | Sensitive psychological, biometric, medical, or intimate data | Psychological profiles, mental health signals, affective inference, biometric markers, health data, identity verification evidence | Critical category. Requires explicit human authorization and must not be used with real data in this block. |
| C7 | Regulated, production-critical, or existential-risk operational data | Real credentials, production secrets, live customer data, production control planes, legal identity records, payment instruments | Critical category. Blocked unless future explicit authorization defines exact secure flow and evidence. |

## C0-C3 Rules

C0-C3 data may be used only when all conditions are true:

- The action is within the approved block, repository, path, PR, branch, or connector scope.
- The operational mode allows the action.
- The connector or tool is authorized for the action.
- The data is not mixed with C4-C7 data.
- Required evidence is recorded.
- No production, external communication, live automation, spend, permission change, or sensitive exposure is triggered.

## C4-C7 Rules

C4-C7 data requires explicit human authorization before:

- Access.
- Modification.
- Transfer.
- External exposure.
- Internal operational use by a live or semi-live agent.
- Use in prompt context, test fixtures, examples, generated documentation, logs, traces, or automation state.
- Connector execution that could read, write, infer, enrich, summarize, classify, publish, share, or retain the data.

If real C4-C7 data appears unexpectedly, NEOS/NEXUS must stop processing it, avoid reproducing it, and escalate.

## Sensitive Psychological Data

Sensitive psychological data is classified as C6 when it includes or implies:

- Mental health conditions or signals.
- Psychological traits, vulnerabilities, assessments, or profiles.
- Emotional inference tied to an identifiable person.
- Cognitive, behavioral, biometric, or intimate data.
- Data used to influence, target, evaluate, or score a person psychologically.

Sensitive psychological data is critical even when inferred rather than directly supplied. It must not be used with real data in this block.

## Operational Prohibitions for This Block

This block prohibits:

- Real C4-C7 data in examples, fixtures, prompts, logs, test data, or documentation.
- Secrets, tokens, passwords, credentials, or production keys.
- Accessing private mailboxes, calendars, Drive files, billing accounts, identity records, or customer systems.
- Transferring sensitive data between tools or connectors.
- Training, fine-tuning, evaluating, or operating agents on real sensitive data.
- Publishing, sharing, or exposing sensitive data externally.

## Mixed Data Rule

When lower-class data is combined with higher-class data, the combined artifact inherits the highest data class present or inferable.

For example, a C2 technical note becomes C4 or higher if it includes private contact details, mailbox content, calendar context, account identifiers, psychological signals, credentials, billing data, or production customer records.

## Minimum Evidence for Data Use

Before any authorized C4-C7 handling in a future block, the evidence record must include:

- Data class.
- Source connector.
- Affected object.
- Purpose.
- Scope.
- Authorizing party.
- Timestamp.
- Retention or deletion expectation.
- Transfer boundary.
- Redaction or minimization method.
- Result and reversibility.

Without sufficient evidence, the action must be blocked or escalated.
