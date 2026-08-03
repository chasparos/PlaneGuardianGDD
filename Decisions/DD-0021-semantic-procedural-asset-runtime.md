# DD-0021 — Semantic Procedural Asset Runtime

- **Status:** Accepted
- **Date:** 2026-08-03
- **Affected documents:** [Semantic Procedural Asset Architecture](../Technical/Semantic_Procedural_Asset_Architecture.md), [Lore Map and Affinity Wheels](../Procedural/Lore_Map_and_Affinity_Wheels.md), [Land and Attachment Visual Contract](../Art/Production_Guides/Land_and_Attachment_Visual_Contract.md), [Client and Server Architecture](../Technical/Client_Server_Architecture.md)

## Context

PlaneGuardian requires parametric Lands and attachments whose geometry,
materials, and effects coherently express the same semantic profile used by
mechanics, naming, and lore. Allowing each shader to interpret every Lore Map
wheel would duplicate policy, create inconsistent palettes, and make structural
changes such as leafless vegetation a rendering concern.

The asset library also needs to carry declarative glTF metadata while allowing
trusted Java implementations to discover new parameters and generator
algorithms in the dedicated asset repository.

## Decision

Card semantics are resolved on the CPU through a versioned pipeline:

```text
Card semantic profile
  -> resolved visual profile
  -> asset-family parameter adapter
  -> geometry, material, and VFX recipes
```

Shaders receive role-based palettes and bounded render parameters rather than
the complete Lore Map. Structural differences use generated geometry or
explicit variants. Materials preserve jMonkeyEngine PBR lighting.

Every semantic family remains available, but Salience, card relevance, asset
role, and Complexity determine which influences become visible. Elemental
Affinity, Ethos, and Manifestation normally carry the strongest direct visual
weight for natural Lands; World Relation modifies form and condition; Magical
Tradition dominates explicitly magical or constructed assets; Cosmic
Provenance is usually conditional.

glTF `extras` contain versioned declarative roles, sockets, surface contracts,
and variant metadata. They do not contain unrestricted executable scripts.

The asset repository produces a paired data library and trusted runtime JAR.
The JAR is initially a normal pinned client dependency and may register
generators through Java's service-provider mechanism. Runtime bytecode
generation and dynamically loaded asset code are not part of the initial
architecture. Signed, hash-verified hot-loaded generator bundles may be added
later if they provide a concrete operational benefit.

The Deciduous Great Tree is the first reference generator. It validates spline
geometry, density-field foliage, optional features, semantic conversion, PBR
materials, LOD, deterministic substreams, and off-color host integration.

## Rationale

A centralized resolver preserves semantic consistency while asset-family
adapters retain the freedom to express the same concept differently. Separating
geometry, materials, and VFX prevents expensive invisible geometry and keeps
silhouette authoritative at gameplay scale.

Pairing data with trusted compiled generators allows the asset repository to
develop parameters and algorithms without turning the asset file into a script
container. Ordinary dependency management is simpler to debug, package,
validate, and reproduce than early dynamic class loading or runtime-generated
bytecode.

The Great Tree exercises most requirements while remaining visually easy to
judge across Life, Death, Order, Chaos, Elemental, Manifestation, Magical, and
host-affinity variations.

## Consequences

- Semantic resolver, adapter, generator, shader, and asset versions participate
  in visual fingerprints and cache keys.
- Asset-family adapters require contribution tracing so parameter outcomes can
  be explained and tested.
- Asset generators emit stable roles, sockets, variant groups, semantic masks,
  LODs, and fallbacks rather than relying on display node names.
- Biomes are derived semantic archetypes with continuous parameters, not the
  sole input to island generation.
- Island layers and asset features use named deterministic random substreams.
- Mutable damage, dormancy, weather, and curses remain separate from intrinsic
  semantic identity.
- The game client and asset runtime share a small, explicitly versioned
  service-provider contract.
- Loading third-party or community-supplied executable generator code remains
  outside the accepted scope.
