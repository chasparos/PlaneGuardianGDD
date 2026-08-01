# DD-0011 — Manifestation Wheel

- **Status:** Accepted
- **Date:** 2026-08-01
- **Affected documents:** [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md), [Lore Map and Affinity Wheels](../Procedural/Lore_Map_and_Affinity_Wheels.md), [Manifestation Wheel and Flavor](../Procedural/Manifestation_Wheel_and_Flavor.md)

## Context

The original Manifestation axes used Material--Ethereal and
Rooted--Wandering. Material--Ethereal overlapped too closely with the
Earth--Aether elemental opposition. The hidden semantic wheels need clear,
exclusive responsibilities even if players never see their underlying
coordinates.

Manifestation needs to answer how and where a card exists without deciding
what elemental force resonates within it.

## Decision

The Manifestation wheel uses two axes:

- **Embodied--Incorporeal:** whether presence depends upon a body or persists
  without one;
- **Rooted--Wandering:** whether presence is bound to a locus or moves between
  loci.

Its primary regions are:

- **Foundation:** Embodied and Rooted;
- **Imprint:** Incorporeal and Rooted;
- **Pilgrimage:** Embodied and Wandering;
- **Drift:** Incorporeal and Wandering.

Earth--Aether continues to describe elemental resonance. It does not imply a
body, an anchor, or mobility. Manifestation may influence physicality,
anchoring, movement, targeting, summoning, banishment, and naming, while
exact mechanics remain future work.

As with the other wheels, Manifestation uses one Salience value and may use
an optional Focus. Correlations with elements, card families, and locations
are soft priors unless another rule explicitly makes them constraints.

## Rationale

This separation allows an earthen memory, a wandering mountain, an embodied
aether construct, or a rooted ghost without semantic contradiction. The
wheel applies meaningfully to creatures, lands, structures, relics, actions,
and events while retaining a distinct question that other wheels do not
answer.

## Consequences

- Naming and lore may use body, presence, anchor, locus, journey, and passage
  vocabulary without treating those ideas as elements.
- Mechanics can distinguish destroying a body from severing an anchor or
  dispersing an incorporeal presence.
- Generation tests should include counterexamples that separate
  Earth--Aether from Manifestation.
- Detailed anchor types, movement rules, and targeting consequences remain
  open design work.
