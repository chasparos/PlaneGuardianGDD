# DD-0020 — 3D Land and Attachment Visual Contract

- **Status:** Accepted
- **Date:** 2026-08-02
- **Affected documents:** [Visual Identity and Main Stage](../Art/Visual_Identity_and_Main_Stage.md), [Land and Attachment Visual Contract](../Art/Production_Guides/Land_and_Attachment_Visual_Contract.md), [Card Zones and Attachments](../GDD/Card_Zones_and_Attachments.md)

## Context

Early concepts successfully established a painted high-fantasy tabletop look,
but they also contained detail that would be expensive to reproduce across a
large procedural card space in real-time 3D. Initial attachment concepts allowed
the host Land to determine too much of an attached card's appearance, which
would weaken card identity and make opposed combinations appear impossible.

The game must support combinations such as a Verdant Oak attached to a Death
Land. The result should look integrated without turning the Oak into an undead
or host-colored replacement.

## Decision

Land and attachment visuals use **dual authorship**.

The Land owns terrain, biome, primary natural landmarks, empty slot treatment,
and local contact parameters. The attached card owns its model, silhouette,
dominant materials, palette, native animation, and operational effects. The
host influences only a bounded integration seam through edge tint, contact
decals, small overlays, reflected light, and limited interaction effects.

An attachment should remain approximately 80--90% visually itself; the host
contributes approximately 10--20% integration. These figures are an art-direction
heuristic, not a literal blend calculation.

All visuals are designed for real-time 3D. Silhouette, heightmap, broad material
zones, and reusable modular assets take priority over microdetail. Concept art
does not authorize one-to-one reproduction of every painted feature. Unique
geometry, props, lights, particles, animation, and nested visual detail must
justify their gameplay-scale readability and production cost.

## Rationale

Preserving attachment identity makes card ownership and surprising combinations
visually meaningful. Restricting host influence to the contact seam allows a
shared shader and overlay system to integrate arbitrary legal pairings without
requiring bespoke models for every Land/attachment combination.

An explicit 3D detail budget keeps the painted direction feasible for a small
art team and a procedurally large card space. Large shapes and materials also
remain more readable from the Main Stage camera than dense concept-art detail.

## Consequences

- Attachment assets require a host-blend mask plus a small contact and overlay
  contract.
- Lands expose slot transforms, host-palette parameters, and bounded reaction
  effects rather than regenerating attached models.
- Off-color attachments remain visibly off-color and mechanically legal unless
  a rare explicit hard restriction says otherwise.
- Biome integration uses reusable decals, edge tint, overlays, and VFX; it does
  not replace the attachment's dominant palette or silhouette.
- Land production prioritizes a heightmap, two or three landmark meshes, broad
  material identity, and sparse reusable dressing.
- Concept reviews must distinguish aspirational mood from approved 3D asset
  complexity.
- Low-detail, effects-disabled, and gameplay-camera validation become required
  parts of visual review.
