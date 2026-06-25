# Registries

Registries are the canonical control plane for NEOS operational knowledge.

They define what tools, connectors, capabilities, permissions and runtimes exist,
who owns them, what risks they introduce and what evidence is required before
they can be considered active.

## Registry System v0.1.0

Registry System v0.1.0 establishes five canonical registries:

| Registry | Canonical file | Purpose |
|---|---|---|
| Tool Registry | `registries/tool-registry.md` | Catalog executable tools and their governed capabilities. |
| Connector Registry | `registries/connector-registry.md` | Catalog external systems connected to NEOS. |
| Capability Registry | `registries/capability-registry.md` | Define normalized capability identifiers. |
| Permission Registry | `registries/permission-registry.md` | Define actions requiring human authorization. |
| Runtime Registry | `registries/runtime-registry.md` | Catalog execution runtimes and their allowed roles. |

## Operating rules

- Every operational action must map to at least one capability.
- Every capability must map to an owner layer.
- Write, destructive, financial, credential, production and external-delivery
  actions must map to a permission.
- Every active tool, connector or runtime must have an evidence requirement.
- Registry changes require an entry in `logs/DECISION_LOG.md` and, when executed,
  corresponding evidence in `logs/EVIDENCE_LOG.md`.

## Status lifecycle

| Status | Meaning |
|---|---|
| Draft | Proposed but not yet approved for use. |
| Pending authorization | Defined but blocked until human authorization is granted. |
| Active | Approved for use under the stated permissions and evidence requirements. |
| Deprecated | Still documented but no longer preferred. |
| Retired | Removed from operational use. |

## Related specification

See `docs/registries/registry-system.md` for the full v0.1.0 contract.
