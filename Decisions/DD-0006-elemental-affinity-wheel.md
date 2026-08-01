# DD-0006 — Elemental Affinity Wheel

- **Status:** Accepted
- **Date:** 2026-08-01
- **Affected documents:** [Lore Map and Affinity Wheels](../Procedural/Lore_Map_and_Affinity_Wheels.md), [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md)

## Context

The Elemental Affinity wheel needs a cohesive high-fantasy topology that supports opposition, adjacency, compounds, names, visuals, resources, damage, and resistance. Physical–Spiritual was considered as an elemental pair but overlaps effect delivery and the Manifestation wheel. Lightning, poison, disease, and decay also need clear classification.

## Decision

The Elemental Affinity wheel contains eight foundational elements in circular order:

```text
Radiance, Fire, Air, Aether, Shadow, Ice, Water, Earth
```

Elements across the center form the oppositions Radiance–Shadow, Fire–Ice, Air–Water, and Earth–Aether. Earth represents matter and embodiment; Aether represents spirit, magical medium, and transcendence. Aether is distinct from the Astral Essence resource.

Lightning and similar phenomena are derived manifestations of multiple affinities. Poison, disease, and decay are effect families shaped by elements and other semantic wheels. Physical and Spiritual are delivery modes rather than elemental sectors.

## Rationale

- Establish four clear oppositions and meaningful circular adjacency.
- Preserve a recognizable high-fantasy elemental vocabulary.
- Prevent the Elemental wheel from absorbing concepts governed by other wheels.
- Allow compound effects to inherit coherent mechanics, names, and visuals.
- Separate what an effect is from how it is delivered and what condition it causes.

## Consequences

- Radiance and Shadow cannot be treated as automatic moral alignment.
- Opposed-element compounds require a relationship mode and may consume complexity budget.
- Damage and resistance design must account for affinity, delivery, form, and condition as separate layers.
- Derived-manifestation thresholds and Elemental sector boundaries remain to be specified.
