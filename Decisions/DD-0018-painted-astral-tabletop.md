# DD-0018 — Painted Astral Tabletop

- **Status:** Accepted
- **Date:** 2026-08-02
- **Affected documents:** [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md), [Visual Identity and Main Stage](../Art/Visual_Identity_and_Main_Stage.md)

## Context

PlaneGuardian needs a high-fantasy identity that makes cards feel as if they
become worlds while remaining achievable for a very small art team. A
semi-realistic direction would magnify asset, animation, material, and
procedural-generation defects. The Main Stage must also communicate Plane
state without becoming visually noisy.

## Decision

PlaneGuardian uses a **painted astral tabletop** style: stylized high-fantasy
islands rendered like hand-painted miniatures over an animated cosmic Void.
Strong silhouettes, exaggerated landmarks, broad painterly value shapes,
controlled palettes, modular assets, and procedural composition take priority
over realism and fine geometric detail.

Only Lands form ordinary floating hex islands. Narrow Void gaps and bridges
make adjacency visible. The Void is a dark contemplative deep-field-inspired
stage whose dust, light, palette, and ornament adapt subtly to the current
Plane.

Size, power, Stability, prosperity, affinity, and maturity use different
visual channels. Permanent Seed maturity changes modular structure and
silhouette; current Plane condition changes lighting, motion, activity, and
effects. Every Seed maturity stage must remain distinguishable as a solid
silhouette while preserving its original core identity.

Rarity, Quality, affinity, family, cooldown, and unique status use separate
card-frame channels. Procedural card art uses layered painted backgrounds,
readable silhouettes, modular morphology, affinity treatment, and versioned
deterministic composition.

## Rationale

The hybrid style preserves high-fantasy richness and card-game clarity while
allowing a reusable asset kit to produce many coherent islands, portraits, and
Seeds. Distinct visual channels make Plane state legible and prevent every
metric from becoming another brightness or color effect.

## Consequences

- The first concept work should test the Main Stage, card-frame separation, and
  Seed summoning before expanding the asset library.
- Camera freedom, geometry, lighting, and materials should support a composed
  diorama rather than unrestricted realism.
- Seed growth requires modular cores, foundations, crowns, anchors, halos, and
  orbitals instead of bespoke complete models.
- Functional UI contrast and accessibility remain stable while affinity and
  Plane identity alter accents and ornament.
- Art generation and caches must be pinned to a visual-generator version.
