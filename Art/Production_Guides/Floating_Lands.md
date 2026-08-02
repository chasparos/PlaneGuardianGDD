# Floating Lands Production Guide

- **Status:** Initial guide derived from approved concept
- **Reference:** [Main Stage Concept 01](../Concepts/Main_Stage/README.md)

## Purpose

Floating Lands must communicate card identity and Plane topology from the Main
Stage camera before optional structures, effects, or interface details are
considered.

## Construction grammar

Each ordinary Land combines:

```text
hex footprint
+ heightmap family
+ cliff profile
+ underside profile
+ biome surface
+ 2--3 silhouette landmarks
+ optional attachment foundations
+ affinity and state layers
```

The footprint preserves adjacency. The heightmap supplies the primary identity:
ridges, terraces, gullies, pools, cliffs, slopes, plateaus, or natural paths.
Biome landmarks reinforce it rather than replace it.

## Silhouette rules

- The Land must remain recognizable as a solid silhouette at gameplay scale.
- Favor two or three large landmarks over many small props.
- Give flatter Lands an asymmetric rear-horizon landmark.
- Vary landmark height and placement across neighboring Lands.
- Preserve crisp island-to-Void edges before atmosphere is applied.
- Use several cliff and underside families to avoid identical rock skirts.

## Development rules

Wild is the default. Buildings, fields, walls, shrines, and similar development
normally originate from attached cards. A civilized biome may include limited
intrinsic development when that identity is mechanically meaningful.

## Validation questions

1. Can the biome be identified without its texture color?
2. Does the island still read after all optional attachments are removed?
3. Is its outer silhouette distinct from both neighboring Lands?
4. Are the attachment foundations visible without resembling buildings?
5. Can atmosphere be disabled without exposing an unclear boundary?
