# DD-0001 — Deterministic Cards

- **Status:** Accepted
- **Date:** 2026-08-01
- **Affected document:** [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md)

## Context

PlaneGuardian treats every card as a procedurally generated artifact with a permanent identity. Storing complete generated definitions for every card would duplicate information and weaken reproducibility.

## Decision

Every card must be reconstructable from its GUID or GUIDs and a versioned generation specification. Persistent storage holds identity and mutable state, such as ownership, cooldowns, inventories, and history, rather than redundant generated statistics.

## Rationale

- Minimize persistent storage.
- Make card generation reproducible and verifiable.
- Support vast procedural variety.
- Keep the same card consistent across clients and services.

## Consequences

- Generation rules and their versions become compatibility-critical data.
- Random streams must be deterministic and isolated by purpose.
- Changing a released generator requires an explicit migration or legacy-generation policy.
