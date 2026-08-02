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

## Visual Identity

The Main Stage presents the current Plane as a painted high-fantasy tabletop
diorama. Procedurally composed floating hex islands hang over a dark,
deep-field-inspired Void and connect through narrow bridges that communicate
adjacency and Stability. The current Plane's affinity and emergent identity
shift the Void, UI accents, island materials, particles, and ambient motion
without compromising readability.

Plane size, power, Stability, prosperity, and maturity use distinct visual
channels. A Seed matures through modular structural stages that change its
silhouette while transient state changes lighting, motion, energy, and visible
activity. Card frames separately communicate family, rarity, Quality,
affinity, cooldown, and unique status.

See [Visual Identity and Main
Stage](../Art/Visual_Identity_and_Main_Stage.md).

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

## Planned Families and Tags

Top-level card families should describe deployment grammar. The current
working families are Plane Seed, Land, Enhancement, Entity, Action,
Operation, Event, and Relic. Creature, Hero, and Squad are Entity subtypes;
Structure, Facility, Enchantment, Location, Fortification, and similar
concepts are normally Enhancement subtypes or tags rather than separate
deployment families. Final player-facing terminology remains open.

Leader is a capability rather than a separate card family. A Leader
assigned to defense becomes the General; a Leader assigned to an attack
becomes the Expedition Commander. Army and Formation are configured
combat structures rather than card types.

Only Lands create ordinary Plane hexes. Other cards occupy explicit zones,
attach through broadly typed host slots, or contribute through Plane-wide
configurations. Hard compatibility constraints are rare; most relationships
use upkeep, Stability, bonuses, and penalties so a large theoretical card
space remains practically usable.

Each owned copy is a distinct card instance and may occupy only one
committed role. Owning multiple copies permits multiple deployments where
budgets and other rules allow.

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
-   Manifestation: Embodied--Incorporeal and Rooted--Wandering

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

Manifestation describes how and where a card exists: whether its presence
is Embodied or Incorporeal, and whether it is Rooted or Wandering. Its
primary regions are Foundation, Imprint, Pilgrimage, and Drift.
Earth--Aether remains an elemental opposition: Earth does not require an
embodied or rooted presence, and Aether does not require an incorporeal or
wandering one.

See [Manifestation Wheel and
Flavor](../Procedural/Manifestation_Wheel_and_Flavor.md).

Magical Tradition describes how an effect is accomplished. Artifice uses
controlled Arcane method, Sorcery uses instinctive Arcane power, Ritual
uses controlled Primal tradition, and Wilding expresses instinctive Primal
power. Its exact center is Mundane: labor, craft, discipline, ingenuity,
and time achieve the result without supernatural technique. Mundane effects
tend to trade lower magical or exotic resource costs for longer completion
times or cooldowns.

See [Magical Tradition Wheel and
Flavor](../Procedural/Magical_Tradition_Wheel_and_Flavor.md).

Cosmic Provenance describes the greater authority, realm, or lineage from
which a card derives identity. Divine and Infernal are provenance rather
than morality. Its exact center is Worldly or Unaligned: independence from
both Heaven and Hell may itself be highly salient.

Each Universe generates an asymmetric cosmology. Its pantheon is a
relational wheel or network of gods with strong Lore Map profiles,
oppositions, alliances, offices, and domains. Hell is a hierarchy of
inherited, specialized, contested, and usurped authority. Associated cards
combine their own identity with a relationship-weighted influence from a
god or infernal rather than becoming copies of that patron.

See [Cosmic Provenance and
Cosmology](../Procedural/Cosmic_Provenance_and_Cosmology.md).

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

The order of placement determines position and activation priority. Lands
activate as a prefix of that ordered list for as long as the Plane can pay
their adjusted Astral Essence upkeep.

Static adjacency rules calculate local Stability while the player builds.
They distinguish Peers in the same ring, inward Lands being supported, and
outward Lands providing support. Stability modifies Essence upkeep before
activation is resolved. Card abilities may ignore, halve, double, reverse,
or otherwise use adjacency effects. The builder shows base upkeep,
adjacency modifiers, final upkeep, and the resulting active extent.

A generic Land contributes its Lore Map profile to Plane affinity, provides
baseline lower-tier storage, pays standard Essence upkeep, and produces 1
biome-appropriate Tier I resource per Plane Day. Additional production,
tags, triggers, capacities, abilities, and attachment slots consume generated
Power and Complexity budgets. Downsides may release discounted Power budget.

Only Lands create ordinary hex tiles. Approximately 20% of generated Lands
provisionally receive one Enhancement slot and 0.1% receive two. Slots consume
generation budget and normally increase upkeep even while empty; attached
cards add their own upkeep. Slotless Lands retain budget for stronger
intrinsic identity. Structures and Facilities are normally Enhancement
subtypes or tags rather than top-level card families.

Lands also influence Plane-wide deployment budgets and eligibility, including
the recurring Operations pile, Rift defense, Battle Events, troop use, and
other systems. Local attachment capacity, global deployment budget, and
eligibility are separate rules.

See [Card Zones and
Attachments](Card_Zones_and_Attachments.md) and [Mechanical Generation
Budget](../Procedural/Mechanical_Generation_Budget.md).

Every Plane Seed contains a Rift through which attackers, thieves,
traders, and guests enter. The Guardian configures a standing defensive
army around the Rift so combat can resolve without the player being
online.

------------------------------------------------------------------------

# 8. Resource Economy

Resources provisionally belong to several tiers:

-   Tier I natural or foundational materials
-   Tier II refined or prepared goods
-   Tier III magical reagents and materials
-   Tier IV planar materials
-   Tier V mythic resources

Routine needs are assumed rather than charged as universal resource taxes.
Explicit resources should represent strategic demands, distinctive
appetites, useful conversion choices, trade, timing, or card-enabling
requirements. Most routine production chains should remain short.

Astral Essence sustains reality itself.

Every Plane Seed generates Astral Essence.

Most Lands consume it as upkeep.

Dormant Lands cease producing and using active abilities until upkeep can
again be paid. Structural storage normally remains available.

Each resource has its own capacity. A normal Land provisionally contributes
2 capacity for every Tier I and Tier II resource, 1 for every Tier III
resource, and none for Tier IV or Tier V. Better Lands may intrinsically
store 1 of each higher-tier resource. Safe Storage is a protected subset of
capacity that cannot be plundered and requires no manual allocation.

Excess resources remain as exposed overflow rather than being silently
destroyed. Overflow cannot increase, is vulnerable to plunder, and may
attract occasional AI-controlled smash-and-grab attacks through the Rift.
These attacks obey lazy simulation and resolve against the standing defense.

The Plane also has an ordered Economic Operations Pile. Only its top card
may activate. If that card is unaffordable, fails a printed requirement, or
remains on cooldown, the pile stops until the player fixes the engine or the
blocker becomes ready. A successful Operation pays its costs, resolves,
enters cooldown, and moves to the bottom. Cards within a pile never execute
in parallel; exceptionally rare effects may grant a second independent pile.

See [Plane Economy and
Operations](../Economy/Plane_Economy_and_Operations.md).

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
enter cooldown on their home Plane's local clock. A deployed defender on cooldown remains
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

Plane Time and Real Time are distinct clock domains. Deployed cards and
runtime Effects experience their containing Plane's local time. The Guardian's
player-space Action Deck and account-level systems use authoritative Real
Time.

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

An Action that advances a Plane by one week performs a genuine week of local
simulation: production, upkeep, healing, deployed cooldowns, Operations,
Events, storage, overflow, and hazards all advance. The Action's own
player-space cooldown remains on Real Time.

Combat resolves outside elapsed time. Battle turns are ordered resolution
steps rather than Plane-time durations. Attacking cards do not travel to or
remain inside the target Plane; combat applies consequences to their home
instances. Persistent cross-Plane interaction creates a runtime Effect on the
target, which uses the target Plane's time and retains provenance from its
source.

See [Time, Combat, and Cross-Plane
Effects](Time_Combat_and_Cross_Plane_Effects.md).

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

The target client is Java using jMonkeyEngine 3. The authoritative server is a
pure Java NIO TCP service. Development persistence uses H2 behind explicit
repository interfaces and migrations; the final production database remains
open, with PostgreSQL the preferred current direction.

Generated card data should be reproducible from GUIDs.

Persistent storage should contain only mutable state such as ownership,
cooldowns, inventories, and timestamps.

The client flow is Splash, Loading, Login or Account Creation, Game Menu, and
Main Stage. First-Plane onboarding occurs inside the Main Stage through Seed
summoning, a semantic questionnaire, a coherent common starter collection,
and a special Action that generates a slightly higher-Quality Hero with
Leader.

Starter families are selected through authoritative domain-separated
generation contexts rather than by modifying completed hash bytes.

See [First Plane Onboarding](First_Plane_Onboarding.md) and [Client and Server
Architecture](../Technical/Client_Server_Architecture.md).

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

## [DD-0011 --- Manifestation Wheel](../Decisions/DD-0011-manifestation-wheel.md)

Embodied--Incorporeal and Rooted--Wandering describe how a card is
present and what binds that presence to the world, independently of its
elemental resonance.

## [DD-0012 --- Magical Tradition Wheel](../Decisions/DD-0012-magical-tradition-wheel.md)

Arcane--Primal and Controlled--Instinctive describe the method by which
an effect is accomplished. Their exact center is deliberately Mundane and
trades supernatural shortcuts for labor and time.

## [DD-0013 --- Cosmic Provenance and Cosmology](../Decisions/DD-0013-cosmic-provenance-and-cosmology.md)

Divine--Infernal provenance opens into a Universe-seeded relational
pantheon and hierarchical Hell, with Worldly or Unaligned identity at the
center. Cosmological powers inhabit and influence the Lore Map rather than
defining it.

## [DD-0014 --- Plane Economy Foundations](../Decisions/DD-0014-plane-economy-foundations.md)

Plane economy is governed by static adjacency Stability, ordered prefix
activation, a deliberately blocking sequential Operations Pile,
per-resource storage with protected capacity, and exposed overflow that may
attract opportunistic AI raids.

## [DD-0015 --- Card Zones, Attachments, and Commitment](../Decisions/DD-0015-card-zones-attachments-and-commitment.md)

Only Lands create ordinary hexes. Other cards use explicit zones and broadly
typed attachment slots; each owned instance may occupy only one committed
role. Hard compatibility constraints remain rare.

## [DD-0016 --- Mechanical Generation Budget](../Decisions/DD-0016-mechanical-generation-budget.md)

The generic Land is the baseline chassis. One Ability Value Unit measures the
expected value of one additional Tier I resource per Plane Day; input credit
does not exceed consumed reference value, and conversion margin is purchased
with Power budget.

## [DD-0017 --- Clock Ownership and Timeless Combat](../Decisions/DD-0017-clock-ownership-and-timeless-combat.md)

Deployed state uses Plane Time, player-space Actions use Real Time, combat
consumes no elapsed time, and cross-Plane interactions transfer consequences
as target-local runtime Effects rather than moving cards.

## [DD-0018 --- Painted Astral Tabletop](../Decisions/DD-0018-painted-astral-tabletop.md)

The game uses modular, painterly high-fantasy dioramas over an adaptive cosmic
Void. Permanent Seed maturity changes silhouette, while current Plane state
changes lighting, activity, cohesion, and effects.

## [DD-0019 --- Java Platform and First Plane Flow](../Decisions/DD-0019-java-platform-and-first-plane-flow.md)

The jME3 client and pure Java NIO server support a Main-Stage onboarding flow
whose domain-separated starter generation guarantees a Seed, coherent common
cards, and a first Leader without post-processing hashes.

## [DD-0020 --- 3D Land and Attachment Visual Contract](../Decisions/DD-0020-3d-land-and-attachment-visual-contract.md)

Land and attachment visuals use dual authorship. Attached cards retain their
model, silhouette, materials, palette, and native effects; the host supplies
only a bounded integration seam. Real-time 3D production prioritizes heightmap,
silhouette, broad materials, and reusable modular assets over concept-art
microdetail.

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
