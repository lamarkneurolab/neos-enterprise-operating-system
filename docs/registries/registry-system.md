# NEOS Registry System v0.1.0

The NEOS Registry System is the canonical source of operational metadata for
tools, connectors, capabilities, permissions and runtimes.

## Objective

Registry System v0.1.0 turns registry placeholders into governed, auditable
operational records. The system exists to answer five questions before NEOS
executes work:

1. What component is being used?
2. What capability does it provide?
3. What permission is required?
4. What runtime is allowed to execute it?
5. What evidence proves the action was completed?

## Canonical registries

| Registry | File | Required identifier prefix |
|---|---|---|
| Tool Registry | `registries/tool-registry.md` | `tool.` |
| Connector Registry | `registries/connector-registry.md` | `connector.` |
| Capability Registry | `registries/capability-registry.md` | Capability namespace such as `repository.` or `evidence.` |
| Permission Registry | `registries/permission-registry.md` | `permission.` |
| Runtime Registry | `registries/runtime-registry.md` | `runtime.` |

## Minimum record contract

Every registry record must include:

| Field | Requirement |
|---|---|
| ID | Stable identifier. It must not be renamed after activation without a decision log entry. |
| Name | Human-readable label. |
| Purpose | Clear operational reason for existence. |
| Owner Layer | NEOS layer accountable for the record. |
| Risk Level | Low, Medium, High or Critical. |
| Authorization | Human authorization rule or permission reference. |
| Evidence | Required proof for activation or execution. |
| Status | Lifecycle state. |

## Authorization policy

Actions require explicit human authorization when they can:

- Create, update or delete repository content.
- Trigger external side effects.
- Modify credentials, permissions, billing or production configuration.
- Publish artifacts outside the local workspace.
- Change registry records from Draft or Pending authorization to Active.

## Evidence policy

Evidence must be recorded in `logs/EVIDENCE_LOG.md` when an action claims
completion. Valid evidence includes:

- Commit hash.
- Pull request URL.
- Command output summary.
- Artifact path.
- External system record ID.
- Approval note from the user conversation.

## Change control

Registry changes must follow this sequence:

1. Update the affected registry file.
2. Update related documentation when the contract changes.
3. Add a decision log entry for material governance changes.
4. Add evidence when the change is executed.
5. Commit the change with a clear message.

## v0.1.0 scope

This version defines the control-plane contract and initial canonical records.
It does not implement an automated registry validation engine.
