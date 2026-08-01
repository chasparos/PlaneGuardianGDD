# PlaneGuardian

## Game Design Document

### Version 0.1

> **Working Draft**

------------------------------------------------------------------------

# Revision History

  Version   Date          Description
  --------- ------------- -----------------------------
  0.1       August 2026   Initial foundational draft.

# Table of Contents

1.  Vision
2.  Design Pillars
3.  Core Gameplay Loop
4.  The World
5.  Core Systems
6.  Card System
7.  Plane Construction
8.  Resource Economy
9.  Action Layer
10. Time & Simulation
11. Technical Philosophy
12. Design Principles
13. Design Decisions
14. Open Questions

------------------------------------------------------------------------

# 1. Vision

## Elevator Pitch

**PlaneGuardian** is a persistent high fantasy card collection and
world-building game where every card is procedurally generated from one
or more globally unique identifiers (GUIDs). Players discover magical
artifacts in the form of cards and assemble them into living Pocket
Planes that evolve over real time.

The game emphasizes discovery, creativity, and long-term progression
rather than traditional deck-versus-deck battles.

------------------------------------------------------------------------

# 2. Design Pillars

## Every Card is Unique

Cards are deterministically generated from GUIDs.

## Players Build Worlds

The primary expression of player creativity is the Plane.

## Persistent Simulation

Planes continue evolving while players are away.

## Lazy Simulation

Simulation occurs only when a Plane is interacted with.

## Discovery is Gameplay

Finding a new card should always be exciting.

------------------------------------------------------------------------

# 3. Core Gameplay Loop

Acquire Cards

↓

Expand Collection

↓

Improve Plane

↓

Generate Resources

↓

Unlock New Opportunities

↓

Repeat

------------------------------------------------------------------------

# 4. The World

Players are **Plane Guardians**, beings capable of stabilizing fragments
of magical reality.

Each fragment manifests as a magical card.

By arranging these fragments around a Plane Seed, Guardians cultivate
persistent Pocket Planes.

------------------------------------------------------------------------

# 5. Core Systems

-   Procedural Card Generation
-   Card Collection
-   Plane Construction
-   Resource Economy
-   Action Deck
-   Persistent Simulation

------------------------------------------------------------------------

# 6. Card System

## Planned Categories

-   Plane Seed
-   Land
-   Structure
-   Facility
-   Action
-   Relic
-   Creature *(future)*
-   Event *(future)*

## Card Axes

### Rarity

Determines global scarcity.

### Quality

Determines craftsmanship and numerical modifiers.

### Efficiency

Measures practical performance.

### Complexity

Determines the procedural design budget available to the generator.

------------------------------------------------------------------------

# 7. Plane Construction

A Plane begins with a Plane Seed.

Land cards are placed in concentric hexagonal rings.

The order of placement determines position.

Future systems will introduce adjacency bonuses and regional effects.

------------------------------------------------------------------------

# 8. Resource Economy

Resources belong to several families:

-   Mundane
-   Refined
-   Magical
-   Divine

Astral Essence sustains reality itself.

Every Plane Seed generates Astral Essence.

Most Lands consume it as upkeep.

Dormant Lands cease functioning until upkeep can again be paid.

------------------------------------------------------------------------

# 9. Action Layer

Players maintain an Action Deck.

Initial capacity: **15 cards**.

Action Cards have real-world cooldowns.

They represent direct intervention by the Plane Guardian.

Examples:

-   Expeditions
-   Resource rituals
-   Time acceleration
-   Exploration
-   Combat
-   Diplomacy

------------------------------------------------------------------------

# 10. Time & Simulation

Each Plane stores:

-   Current State
-   Stored Resources
-   Last Simulation Timestamp

When accessed:

1.  Calculate elapsed real time.
2.  Simulate the delta.
3.  Update Plane state.
4.  Save the new timestamp.

No Plane is continuously simulated.

------------------------------------------------------------------------

# 11. Technical Philosophy

The game favors deterministic systems.

Generated card data should be reproducible from GUIDs.

Persistent storage should contain only mutable state such as ownership,
cooldowns, inventories, and timestamps.

------------------------------------------------------------------------

# 12. Design Principles

## Discovery

Cards should feel like magical artifacts.

## Creativity

Many viable Plane designs should exist.

## Trade-offs

Growth should always require meaningful choices.

## Mystery

Players should never completely understand the procedural universe.

------------------------------------------------------------------------

# 13. Design Decisions

## DD-0001 --- Deterministic Cards

Every card must be reconstructable from its GUID(s).

Reason:

-   Minimal storage
-   Easy verification
-   Infinite procedural variety
-   Consistent generation

------------------------------------------------------------------------

# 14. Open Questions

-   Combat
-   Trading
-   Crafting
-   Creature system
-   Procedural naming
-   Ability generation
-   Multiplayer
-   Procedural art

------------------------------------------------------------------------

# Closing Statement

> **Every card is a fragment of a world. Every player is the architect
> of a universe.**
