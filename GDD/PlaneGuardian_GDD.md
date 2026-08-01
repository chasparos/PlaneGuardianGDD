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
11. Universes, Eras & Eternal Cards
12. Technical Philosophy
13. Design Principles
14. Design Decisions
15. Open Questions

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
-   Creature
-   Hero
-   Squad
-   Event

Leader is a capability rather than a separate card family. A Leader
assigned to defense becomes the General; a Leader assigned to an attack
becomes the Expedition Commander. Army and Formation are configured
combat structures rather than card types.

## Card Axes

### Rarity

Determines global scarcity.

### Quality

Determines craftsmanship and numerical modifiers.

### Efficiency

Measures practical performance.

### Complexity

Determines the procedural design budget available to the generator.

## Semantic Profile

Each card receives a deterministic semantic profile from the shared
**Lore Map**. Applicable affinity wheels contribute a direction,
Extremity, and independent Salience value. Extremity describes how far
the card lies from a wheel's center; Salience describes how important
that wheel is to the card.

The initial semantic families are:

-   Elemental Affinity: Radiance, Fire, Air, Aether, Shadow, Ice,
    Water, and Earth
-   Ethos: Order--Chaos and Life--Death
-   World Relation: Preservation--Transformation and
    Creation--Annihilation
-   Cosmic Provenance: Divine--Infernal
-   Magical Tradition: Arcane--Primal and Controlled--Instinctive
-   Manifestation: Material--Ethereal and Rooted--Wandering

Not every wheel influences every card. Card family and context determine
relevance, while Complexity determines how many influences or tensions
become visible. Mechanics, procedural names, art, and lore consume the
same profile so they describe a coherent artifact. Deliberate opposing
affinities require a relationship such as Equilibrium, Synthesis,
Conflict, Alternation, Suppression, or Paradox.

Each wheel uses one Salience value. Complex cards may receive an optional
Focus that narrows interpretation without becoming another independent
naming branch. Ethos Focus may emphasize Order--Chaos, Life--Death, the
complete wheel, the center, or cycles among its regions.

See [Lore Map and Affinity
Wheels](../Procedural/Lore_Map_and_Affinity_Wheels.md).

See [Ethos Wheel and Naming
Vocabulary](../Procedural/Ethos_Wheel_and_Naming_Vocabulary.md).

World Relation supplies procedural verbs and consequences. Preservation
maintains identity, Transformation changes it, Creation brings something
new into existence, and Annihilation removes something from existence.
Its primary regions are Restoration, Genesis, Excision, and Dissolution.
Death, decay, ordinary destruction, and transportation are not
automatically Annihilation or Creation.

See [World Relation Wheel and
Flavor](../Procedural/World_Relation_Wheel_and_Flavor.md).

Elemental Affinity uses four oppositions: Radiance--Shadow,
Fire--Ice, Air--Water, and Earth--Aether. Compounds such as Lightning
and Magma derive from multiple affinities. Physical and Spiritual are
effect-delivery modes rather than elements; Poison, Disease, and Decay
are generated effect families rather than foundational sectors.

## Origins and Discovery Sources

Players discover cards by supplying sources such as summoning phrases,
locations, crafted formulas, divinations, or arbitrary text. The same
canonical source and source type resolve to the same card during an Era
while copies remain available.

The server protects the mapping from source text to Origin ID so players
cannot mine desirable cards offline. The Origin ID still reconstructs
the complete card deterministically. A separate authoritative ledger
enforces global supply and per-account copy limits.

Knowledge of a productive source may be shared with friends or guilds.
An exhausted source can no longer issue copies, including after a unique
card has been claimed.

See [Card Origins and Protected
Discovery](../Procedural/Card_Origins_and_Protected_Discovery.md).

## Creative Layer

The first discoverer of a unique card receives the right to nominate its
display name and may propose artwork. Every unique card retains a
deterministic fallback presentation. Player contributions affect
presentation only and require provenance, review, reporting,
moderation, and appeal.

Discoverer, creative contributor, and current owner remain distinct in
the card's permanent history. Approved names and artwork may survive
across Eras if the card becomes Eternal.

------------------------------------------------------------------------

# 7. Plane Construction

A Plane begins with a Plane Seed.

Land cards are placed in concentric hexagonal rings.

The order of placement determines position.

Future systems will introduce adjacency bonuses and regional effects.

Every Plane Seed contains a Rift through which attackers, thieves,
traders, and guests enter. The Guardian configures a standing defensive
army around the Rift so combat can resolve without the player being
online.

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

## Combat Actions

An attack requires an Action card and an Expedition Commander. The
Action determines the objective, attacking capacity, success threshold,
payoff or consequence, cooldown, and special rules. Possible objectives
include probing, raiding, harassment, sabotage, pillage, assault, and
siege.

Attack and defense use the same planning concepts: commander, formation,
tactical zones, troops, reserves, support, and Battle Events. A large
economy can sustain greater defensive capacity, but card quality,
synergy, command, and deployment determine effectiveness.

Tactical victory, attrition, and objective completion are separate
results. A Harassment attack may award no plunder while extending the
cooldowns of defeated defenders to prepare for a later Pillage.

Combat snapshots the configured defense when declared. Defeated cards
enter real-world cooldown. A deployed defender on cooldown remains
assigned to its slot and cannot be replaced until ready. Online players
may react to completed battles and prepare for later attacks, but cannot
alter an attack already underway or erase attrition by cycling cards.

The Action Deck supports different play rhythms: active players may use
frequent short-cooldown attacks with small payoffs, while occasional
players may select longer-cooldown Actions with greater capacity and
payoff. Balance should target comparable opportunity over real time.

See [Combat and Raiding](Combat_and_Raiding.md).

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

# 11. Universes, Eras & Eternal Cards

A **Universe** is a persistent historical lineage. An **Era** is a reset
cycle within that Universe. Universe and Era identifiers contribute to
protected source generation, so the same source may reveal different
cards in different Eras or Universes.

At an Era's Reckoning, its results are locked and preserved in a
read-only Hall of Fame. Ordinary active state resets or becomes Legacy
history.

**Eternal** is a lifecycle axis independent of rarity and quality.
Eternal cards preserve identity, mechanics, provenance, approved name,
approved art, and history across Eras. Eternity preserves identity, not
power: promotion never rerolls or strengthens a card.

Paths to Eternity include:

-   Born Eternal
-   Ascended through an Era achievement or limited choice
-   Consecrated through an extraordinary collaborative ritual
-   Honored for historical or community-recognized significance

Each Era has a limited Eternal Budget. Eternal cards reside in an
Eternal Vault and only a limited number may awaken in a new Era, keeping
fresh starts meaningful.

------------------------------------------------------------------------

# 12. Technical Philosophy

The game favors deterministic systems.

Generated card data should be reproducible from GUIDs.

Persistent storage should contain only mutable state such as ownership,
cooldowns, inventories, and timestamps.

------------------------------------------------------------------------

# 13. Design Principles

## Discovery

Cards should feel like magical artifacts.

## Creativity

Many viable Plane designs should exist.

## Trade-offs

Growth should always require meaningful choices.

## Mystery

Players should never completely understand the procedural universe.

------------------------------------------------------------------------

# 14. Design Decisions

## [DD-0001 --- Deterministic Cards](../Decisions/DD-0001-deterministic-cards.md)

Every card must be reconstructable from its GUID(s).

Reason:

-   Minimal storage
-   Easy verification
-   Infinite procedural variety
-   Consistent generation

## [DD-0002 --- Semantic Lore Map](../Decisions/DD-0002-semantic-lore-map.md)

Mechanics, names, art, and lore consume one versioned semantic profile.

## [DD-0003 --- Protected Source-Based Discovery](../Decisions/DD-0003-protected-source-discovery.md)

Player-provided sources map to deterministic cards through a protected,
server-authoritative origin process.

## [DD-0004 --- Universes, Eras, and Eternal Cards](../Decisions/DD-0004-universes-eras-and-eternal-cards.md)

Eras provide renewal, Universes provide continuity, and Eternal cards
provide memory without receiving promotion power.

## [DD-0005 --- Creative Stewardship of Unique Cards](../Decisions/DD-0005-creative-stewardship-of-unique-cards.md)

Unique-card discoverers may nominate reviewed presentation while
deterministic mechanics and fallback presentation remain intact.

## [DD-0006 --- Elemental Affinity Wheel](../Decisions/DD-0006-elemental-affinity-wheel.md)

Eight foundational elements form four oppositions. Compound phenomena
and harmful conditions derive from affinities and other semantic wheels.

## [DD-0007 --- Ethos Salience and Focus](../Decisions/DD-0007-ethos-salience-and-focus.md)

Each wheel retains one Salience value; exceptional cards may use an
optional Focus to create perceptible axis-specific identity.

## [DD-0008 --- Leaders, Generals, and Force Construction](../Decisions/DD-0008-leaders-generals-and-force-construction.md)

Leader is a card capability, General and Expedition Commander are
assignments, and armies are configured forces constrained by capacity.

## [DD-0009 --- Asynchronous Objective Combat](../Decisions/DD-0009-asynchronous-objective-combat.md)

Attacks resolve against standing defenses with separate tactical,
attrition, and objective results; committed cards cannot be replaced
while on cooldown.

## [DD-0010 --- World Relation Wheel](../Decisions/DD-0010-world-relation-wheel.md)

Preservation--Transformation and Creation--Annihilation describe how a
card maintains, changes, creates, or removes identities and existence.

------------------------------------------------------------------------

# 15. Open Questions

-   Detailed combat turns, formations, targeting, and Breach calculation
-   Trading
-   Crafting
-   Creature system
-   Elemental sector widths and boundary behavior
-   Naming lexicon and cultural grammars
-   Ability generation
-   Multiplayer
-   Procedural art
-   Eternal Budget and awakening limits
-   Era reset boundaries

------------------------------------------------------------------------

# Closing Statement

> **Every card is a fragment of a world. Every player is the architect
> of a universe.**
