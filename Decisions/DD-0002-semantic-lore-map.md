# DD-0002 — Semantic Lore Map

- **Status:** Accepted
- **Date:** 2026-08-01
- **Affected documents:** [Lore Map and Affinity Wheels](../Procedural/Lore_Map_and_Affinity_Wheels.md), [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md)

## Context

Independently randomizing statistics, names, art, and lore would frequently produce incoherent cards. PlaneGuardian needs procedural variety with semantic control and room for intentional paradox.

## Decision

All card generators consume a shared, versioned Lore Map. Applicable semantic wheels generate a direction, Extremity, and independent Salience value. Card type and context determine relevance; complexity determines how many influences, poles, and special relationships become visible.

The initial semantic families are Elemental Affinity, Ethos, World Relation, Cosmic Provenance, Magical Tradition, and Manifestation. Naming draws from the same semantic profile as mechanics and art.

## Rationale

- Keep generated properties thematically coherent.
- Give designers control without eliminating discovery.
- Distinguish indifference from committed balance or internal conflict.
- Make unusual combinations explainable through relationships and complexity.

## Consequences

- Lore Map, lexicon, coordinate, and generator versions are compatibility-critical.
- Centered high-Salience cards require relationship modes such as Equilibrium, Synthesis, or Conflict.
- Secondary poles and deliberate paradox consume complexity budget.
- Not every wheel applies to or visibly influences every card.
