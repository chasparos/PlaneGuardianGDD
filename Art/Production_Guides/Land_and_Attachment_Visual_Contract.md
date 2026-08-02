# Land and Attachment Visual Contract

- **Status:** Foundational production direction
- **Related decision:** [DD-0020](../../Decisions/DD-0020-3d-land-and-attachment-visual-contract.md)
- **Concept references:** [Land and Attachment Visual Contract Concepts](../Concepts/Land_Attachment_Contract/README.md)
- **Related guides:** [Floating Lands](Floating_Lands.md), [Attachment Slots](Attachment_Slots.md), [Plane-State Visual Language](Plane_State_Language.md)

## Purpose

PlaneGuardian is rendered as real-time 3D. Concept art establishes hierarchy,
mood, silhouette, and material language; it is not a mandate to reproduce every
painted detail as geometry, a unique prop, a light, a particle emitter, or an
animation.

The production target is a convincing painted tabletop assembled from a small,
versioned, reusable vocabulary. Detail is costly to author, combine, render,
test, cache, and maintain. It must be used where it remains readable and carries
distinct game information.

## Core contract

### The Land owns

- the hex footprint, heightmap, cliffs, and underside;
- biome surface materials and broad palette;
- two or three primary natural silhouette landmarks;
- slot transforms and the empty-foundation presentation;
- local contact parameters such as ash, moss, frost, sand, lichen, reflected
  light, and bounded affinity reactions;
- Plane-state and atmospheric layers that apply to the host.

### The attached card owns

- its primary model and recognizable silhouette;
- its dominant materials, palette, and construction language;
- its native animation and operational effects;
- its gameplay-readable identity across every legal host;
- an authored host-blend mask and a small set of contact or overlay anchors.

### The integration seam owns

- limited edge tint near the attachment base;
- one ground-contact decal or material transition;
- a small overlay such as roots, ash, frost, dust, lichen, or wet stone;
- one bounded interaction effect such as steam, sparks, condensation, or
  reflected light;
- contact shadows and local ambient-occlusion treatment.

As a working heuristic, an attachment should remain about **80--90% itself**.
The host supplies the remaining **10--20% integration seam**. These percentages
describe visual ownership, not a literal shader interpolation value.

Off-color attachments are intentional. A Verdant Oak in a Death Land remains
alive, green, and recognizable. The host may ash its lowest roots or add pale
lichen; it must not turn the entire tree dead, spectral, purple, or skeletal.

## Practical 3D assembly

A first production Land should normally fit this assembly:

```text
heightmap-derived terrain mesh
+ cliff and underside family
+ biome material set
+ 2--3 landmark meshes
+ sparse clustered ground-detail cards
+ zero, one, or exceptional second slot transform
+ state and atmosphere parameters
```

An attachment should normally fit this assembly:

```text
primary model
+ 0--3 modular detail pieces
+ native material set
+ host-blend mask
+ contact anchor
+ 0--2 overlay anchors
+ bounded VFX sockets
```

The exact implementation remains technical work. A likely jME3 approach uses
vertex color or a small mask texture for host blending, material parameters for
the sampled host palette, a projected contact decal, reusable overlay meshes,
and separate lightweight VFX attached to named sockets.

## Visual cue budget

Spend the budget in this order:

| Priority | Cue | Preferred implementation |
| --- | --- | --- |
| 1 | Footprint and heightmap | Shared terrain mesh families and parameters |
| 2 | Primary silhouette | Two or three reusable landmark meshes |
| 3 | Broad material identity | Painted atlases, masks, and restrained shader variation |
| 4 | Attachment identity | One readable primary model and native materials |
| 5 | State and integration | Decals, edge masks, limited overlays and bounded VFX |
| 6 | Secondary dressing | Sparse instanced or clustered reusable props |
| 7 | Close detail | Texture information unless it remains essential at gameplay scale |

Dynamic lights, transparent effects, animated props, unique meshes, nested
attachments, and dense foliage are expensive multipliers. They should be rare,
bounded, and supported by LOD or fallbacks.

## Detail authorization test

Before adding a visual element, ask:

1. Is it readable from the ordinary Main Stage camera?
2. Does it communicate information not already carried by silhouette, material,
   UI, or another effect?
3. Can it be reused across many generated cards or combinations?
4. Does it remain coherent on off-color and semantically opposed hosts?
5. Can it be reduced, instanced, culled, or removed at lower detail levels?
6. Is its authoring, draw-call, shader, memory, animation, and testing cost
   justified by the player-facing gain?

If the answer is no, express it through painted texture, a broader shape, a
shared decal, or omit it.

## Readability limits

- Preserve strong silhouettes before adding small props.
- Do not use atmospheric blending to hide weak geometry.
- Do not let prosperity mean universal prop density or settlement.
- Do not let affinity mean full-model recoloring.
- Do not let every state add brightness, particles, and motion.
- Do not reproduce concept-art microdetail that disappears at gameplay scale.
- Nested attachments must not create unbounded visible model trees.

## Validation views

Review each Land and attachment in:

1. solid-black silhouette;
2. flat unlit materials;
3. ordinary gameplay camera and expected screen size;
4. native-affinity host;
5. strongly off-color host;
6. low-detail and effects-disabled modes;
7. occupied and unoccupied slot states.
