# Plane-State Visual Language

- **Status:** Initial guide derived from approved concept
- **Reference:** [Main Stage Concept 01](../Concepts/Main_Stage/README.md)

## Layering principle

Base island geometry, card-derived attachments, Plane state, and atmosphere are
separate visual layers. A state treatment may enrich a readable island but must
not be required to make its topology or biome understandable.

| Layer | Owns |
| --- | --- |
| Base Land | Footprint, heightmap, cliffs, biome, silhouette landmarks |
| Attachment | Buildings, facilities, shrines, lairs, enchantments, other card-derived landmarks |
| Plane state | Activity, dormancy, Stability, power, prosperity, damage |
| Atmosphere | Mist, smoke, dust, particles, affinity ambience, Void blending |

## Pre-alpha requirements

- **Active:** controlled motion or light at production-relevant features.
- **Dormant:** reduced activity and withdrawn light without hiding the Land.
- **Stable:** aligned islands and complete, quiet bridges.
- **Unstable:** bounded displacement and strained bridge form.
- **Prosperous:** selective cultivation, maintenance, habitation, or activity;
  never universal architectural clutter.
- **Atmosphere disabled:** crisp outer silhouettes and fully readable adjacency.

Plane-state channels remain semantically distinct. Increasing every state value
must not merely add brightness, particles, and props.
