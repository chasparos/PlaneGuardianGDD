# Semantic Procedural Asset Architecture

- **Status:** Foundational architecture; generator algorithms remain implementation work
- **Related decisions:** [DD-0002](../Decisions/DD-0002-semantic-lore-map.md), [DD-0020](../Decisions/DD-0020-3d-land-and-attachment-visual-contract.md), [DD-0021](../Decisions/DD-0021-semantic-procedural-asset-runtime.md)
- **Related documents:** [Lore Map and Affinity Wheels](../Procedural/Lore_Map_and_Affinity_Wheels.md), [Land and Attachment Visual Contract](../Art/Production_Guides/Land_and_Attachment_Visual_Contract.md), [Client and Server Architecture](Client_Server_Architecture.md)

## Purpose

Procedural visuals must make mechanics, names, art, and lore appear to describe
the same card without requiring every mesh, material, or shader to understand
the complete Lore Map. This document defines the boundary between card
semantics and the asset-generation runtime used by the jMonkeyEngine client.

Detailed generator algorithms and implementation constants belong to the
`PlaneGuardianAssets` repository. The GDD records their required behavior and
stable integration contract.

## Resolution pipeline

The client resolves visuals in stages:

```text
Card semantic profile
  -> versioned Land visual profile
  -> asset-family parameter adapter
  -> geometry recipe + material parameters + VFX recipe
  -> jME scene subtree
```

Shaders do not independently interpret all six semantic wheels. A centralized,
versioned resolver first produces a compact visual profile containing a
role-based palette and normalized visual channels. An asset-family adapter then
decides how those channels manifest in vegetation, stone, water, constructed
landmarks, or other assets.

The common contract is the input language, not identical output. Life may
increase foliage on a tree, biological cover on an island, and restorative
effects on a shrine. It does not require a universal `Life` shader branch.

## Three output domains

An asset adapter separates its result into:

1. **Geometry and variants:** silhouette, branch or formation structure,
   presence of foliage, hollows, missing volumes, sockets, and major overlays.
2. **Materials:** role-based palette, roughness, normal response, dryness,
   restrained emission, semantic masks, and host-contact blending.
3. **Effects:** motes, falling leaves, embers, spectral drift, pulses, and other
   bounded motion or atmosphere.

Structural states must not be simulated by hiding fully generated geometry in a
fragment shader. A leafless tree omits its canopy geometry; a sparse tree uses
fewer foliage clusters rather than a transparent full crown.

## Resolved visual profile

The asset layer consumes immutable presentation data rather than gameplay
objects. The initial Land profile should provide:

- a palette with shadow, base, highlight, primary accent, secondary accent,
  and emissive roles;
- eight non-negative Elemental influence weights;
- signed Life--Death and Order--Chaos channels;
- signed Preservation--Transformation and Creation--Annihilation channels;
- signed Embodied--Incorporeal and Rooted--Wandering channels;
- Magical Tradition direction, supernatural strength, and Mundane center
  strength;
- Divine--Infernal bias and independent provenance strength;
- relevant center-relationship modes;
- schema and resolver versions.

Values are resolved and quantized on the CPU. Individual materials receive
only final colors and render-oriented parameters required by their declared
material contract.

## Semantic relevance for Land visuals

All six semantic families remain available, but not every family directly
influences every asset. Apply the existing conceptual rule:

```text
Influence = Salience * CardTypeRelevance * ContextRelevance
```

Then allow the asset family and card Complexity to determine how many
influences become visible.

| Semantic family | Natural terrain | Vegetation | Constructed landmark | VFX |
| --- | --- | --- | --- | --- |
| Elemental Affinity | Primary | Primary | Secondary | Primary |
| Ethos | Secondary | Primary | Secondary | Secondary |
| Manifestation | Primary | Secondary | Secondary | Primary |
| World Relation | Secondary | Secondary | Secondary | Secondary |
| Magical Tradition | Conditional | Conditional | Primary | Primary |
| Cosmic Provenance | Conditional | Conditional | Conditional or Primary | Primary |

Most ordinary assets should visibly express one primary family and one or two
secondary families. Exceptional Complexity may reveal more. Low-ranked wheels
remain latent instead of adding visual noise.

High-Salience centered profiles retain their relationship mode. Equilibrium,
Synthesis, Conflict, Alternation, Suppression, and Paradox require different
composition rules; they must not collapse into an average color or neutral
shape.

## Biome and island generation

A Land's biome is a deterministic consequence of its card family, tags, and
semantic profile. It is not the only input to island generation.

```text
Land semantics
  -> biome archetype + continuous biome parameters
  -> layered island construction
```

The island generator should build independent, versioned layers:

1. foundation silhouette, height field, cliffs, and underside;
2. geology, strata, erosion, cavities, and mineral features;
3. climate and substrate, including temperature, moisture, soil, snow, and
   water;
4. biome cover and ground material;
5. two or three large silhouette landmarks;
6. slot foundations, bridge connections, and gameplay transforms;
7. semantic overlays such as spectral dissolution or elemental emission;
8. mutable Plane and card-instance state.

This permits related but distinct results such as a Life--Water wetland, a
Death--Water drowned fen, or a Fire--Death ash barrens. The biome supplies a
coherent construction grammar while continuous semantics preserve individual
card identity.

Use named random substreams for terrain, geology, biome cover, landmarks,
slots, materials, and effects. Improving vegetation must not move a slot or
change the island's foundational silhouette.

## Asset package contract

The asset system uses glTF as its primary interchange format and may annotate
roots, nodes, meshes, and materials through a versioned PlaneGuardian envelope
in glTF `extras`.

The envelope is declarative. Stable role identifiers describe parts such as
`trunk`, `foliage`, `hollowInterior`, `hostContact`, `attachmentSocket`, and
`ambientVfxSocket`. Variant groups describe mutually exclusive or optional
geometry. Display names remain debugging aids rather than behavioral keys.

`asset_index.json` describes package-level information including:

- stable asset and generator identifiers;
- schema, generator, adapter, and material-contract versions;
- packed-library locations and hashes;
- capabilities and variant groups;
- fallback glTF assets;
- required textures, shaders, masks, LODs, and sockets.

Do not embed unrestricted JavaScript or another general scripting language in
glTF metadata. Repeated asset-local rules may eventually use a small validated
declarative expression vocabulary, but Java adapters should establish the
requirements first.

## Data and runtime delivery

The asset repository should build two paired artifacts:

```text
asset-data library (binary format and filename remain open)
planeguardian-assets-runtime.jar
```

The data library contains the index, glTF assets, textures, masks, material
definitions, shaders, and declarative metadata. The trusted runtime JAR
contains semantic adapters, parameter generators, asset controllers, runtime
geometry generators, and validators.

Initially, the runtime JAR is an ordinary pinned client dependency. Generator
providers may register through Java's standard service-provider mechanism.
Runtime bytecode generation is not required. Dynamically loaded generator JARs
are deferred until signed downloadable bundles provide a concrete benefit.

If hot-loaded bundles are introduced, the client accepts only project-trusted,
hash-verified code compatible with the exact asset service-provider API.
Class-loader separation is an update and discovery mechanism, not a sandbox for
untrusted executable content.

## jMonkeyEngine material contract

Affinity-aware materials preserve jME's standard PBR lighting, shadows, and
scene-light inputs. Semantic processing modifies material inputs such as base
color, roughness, normal strength, opacity where supported, and emission; it
does not replace lighting with an unlit affinity shader.

PlaneGuardian-aware materials should share stable parameter names for:

- palette roles;
- emission strength;
- roughness and normal biases;
- host-blend strength;
- dissolution or spectral treatment;
- semantic motion response.

Vertex colors or compact mask textures identify primary, secondary, emissive,
and host-contact regions. Asset-specific materials may add bounded parameters
such as leaf dryness or fissure glow without redefining the common contract.

Shared loaded materials are immutable templates. The client clones or caches
resolved material instances by template, profile hash, shader version, and
render tier.

## Intrinsic identity, host, and state

Visual composition follows this order:

```text
Generator-native identity
  -> intrinsic card semantics
  -> bounded host-Land integration
  -> mutable instance condition
  -> scene lighting and atmosphere
```

A native Death-aligned tree is not necessarily damaged or dormant. A living
tree temporarily burned or cursed retains its intrinsic identity beneath its
condition. Likewise, an off-color attachment retains its own semantic profile;
the host affects only the integration seam defined by DD-0020.

## Reference generator: Deciduous Great Tree

The first reference implementation should be a large deciduous tree because it
tests structural generation, organic surfaces, optional features, motion, LOD,
and off-color host integration in one readable asset.

Its detailed implementation belongs to `PlaneGuardianAssets`. At minimum it
must demonstrate:

- spline-generated trunk, branches, and major roots;
- deterministic branch hierarchy and independent random substreams;
- a crown density field driving leafless, sparse, and full foliage geometry;
- gameplay-scale foliage clusters rather than individual leaf geometry;
- optional local hollow, moss, vine, flower, and fruit features;
- semantic parameter conversion with an inspectable contribution trace;
- role-based PBR materials and bounded host-contact blending;
- near, gameplay, and distant LODs;
- fixed golden cases covering ordinary, opposed, centered, and off-color
  semantic combinations.

Death plus Creation must remain distinguishable from simple decay, Mundane
high Salience must support impressive non-magical trees, and an intrinsically
verdant tree must remain alive when hosted by a Death Land.

## Determinism and validation

The visual fingerprint includes card identity, Universe and semantic versions,
asset ID, resolver, adapter, generator, shader, and render-tier versions.
Presentation values are quantized before hashing or serialization.

Validation requires:

- identical inputs and versions produce identical resolved parameters;
- named substreams isolate unrelated generation layers;
- geometry contains finite positions, normals, tangents, and bounds;
- LODs preserve primary silhouette and gameplay sockets;
- materials respond correctly to the client's required PBR lighting modes;
- foliage remains stable under mipmapping and normal camera motion;
- native-affinity and strongly off-color hosts are both reviewed;
- historical generator versions remain reproducible or have pinned baked
  fallbacks.

## Open implementation questions

- Exact packed-library binary format and patching strategy.
- Asset service-provider API and Java/jME dependency boundary.
- Persistent cache format for generated meshes and materials.
- Exact PBR shader integration for the selected jME version.
- Per-asset-family triangle, draw-call, generation-time, and memory budgets.
- Final perceptual palette space and gamut mapping.
- Whether a constrained declarative parameter graph becomes useful.
- Whether signed generator bundles must be hot-loadable without restarting.
