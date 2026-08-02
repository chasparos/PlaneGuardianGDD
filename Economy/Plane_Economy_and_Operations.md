# Plane Economy and Operations

- **Status:** Foundational design with provisional values
- **Related decision:** [DD-0014](../Decisions/DD-0014-plane-economy-foundations.md)
- **Related documents:** [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md), [Combat and Raiding](../GDD/Combat_and_Raiding.md)

## Purpose

The Plane economy turns card selection, spatial arrangement, activation order,
and recurring Operations into a coherent engine. It should reward planning and
specialization without requiring the player to simulate routine subsistence.

The core questions are:

1. Which Lands belong together?
2. Which Lands must remain active when Essence is scarce?
3. In what order should the Plane perform economic work?
4. How much of each resource can the Plane retain and protect?

## Design principles

### Strategic demands, not routine needs

People eat, tools wear out, structures receive ordinary maintenance, and
soldiers use mundane equipment. These needs are included in the normal
operation of their cards unless making one explicit creates a meaningful
decision.

Food or Provisions may matter for an expedition, feast, siege recovery,
population surge, unusual appetite, ritual, or trade route. They should not be
a universal hourly tax attached to every creature and army.

### Short routine chains

Most ordinary production uses zero or one refinement step:

```text
Timber -> Lumber
Iron Ore + Coal -> Steel
Herbs -> Medicine
Mana Crystals -> Arcane Dust
```

Longer chains should culminate in something that changes play, such as
awakening a rare Land or enabling a distinctive Leader. They should not exist
merely to reproduce everyday tools at increasing levels of abstraction.

### Broad requirements and substitution

Basic recipes should accept resource families or semantic tags. Exact variants
matter for specialized recipes and exceptional cards.

For example, a generated dragon may accept tribute in Wealth, Gems, Livestock,
Mana Crystals, Spirit Residue, or Relics according to its identity. Building
the small production chain that awakens that dragon's full Leader capability
is meaningful; feeding every ordinary unit is not.

### Place exciting cards before perfect support

A Land should usually provide basic value without every ideal input. Support
may improve output, unlock an ability, satisfy a distinctive appetite, or
activate its strongest form. The player can place a compelling card and then
build toward its full potential.

## Astral Essence and ordered activation

Astral Essence is the Plane's existence budget. The Planar Seed and certain
specialized cards generate it; most Lands require it as upkeep.

The ordered Land list performs three jobs:

- maps cards to hex tiles;
- establishes activation priority;
- defines the Plane's emergency shutdown and recovery order.

After static modifiers are calculated, the Plane pays final upkeep from the
Seed outward in list order. Every successfully funded Land joins the active
prefix. When the next Land cannot be paid, it and every later Land remain
dormant.

Dormant Lands remain configured parts of the Plane. They stop producing and
using active abilities but continue contributing static properties unless a
rule explicitly says otherwise.

## Generic Land chassis

The generic Land establishes the zero point for procedural valuation:

- contributes its semantic profile to the Plane's affinities;
- has a biome or Land type that selects a compatible ordinary output;
- produces 1 Tier I resource per Plane Day;
- provides baseline lower-tier storage;
- pays standard Land Astral Essence upkeep;
- has no attachment slot or additional ability.

These properties are the baseline entitlement for being a Land rather than
positive abilities purchased from its generated Power budget. Generation
budget buys improvements above the chassis. See [Mechanical Generation
Budget](../Procedural/Mechanical_Generation_Budget.md).

## Adjacency Stability

Stability is a visible, derived property of the configured layout rather than
a stored resource. It summarizes compatible, opposed, and otherwise meaningful
adjacency relationships.

```text
Card profiles
+ static adjacency rules
+ printed abilities
= local Stability modifier
= final Essence upkeep
```

The primary mechanical expression of Stability is adjusted Astral Essence
upkeep. Harmonious relationships tend to reduce upkeep; tensions tend to
increase it. This causes unstable layouts to support fewer active Lands through
the existing prefix rule rather than through a second activation currency.

### Static calculation

All configured Lands participate in static adjacency calculation, including
dormant Lands. Dormancy removes production and active effects, not the Land's
presence or metaphysical pressure. This avoids oscillation in which a Land
alternately deactivates, removes its own penalty, and reactivates.

The builder should show before commitment:

- base Essence upkeep;
- each adjacency bonus and penalty;
- printed ability modifiers;
- final Essence upkeep;
- the active prefix and first unsupported Land;
- local and Plane-wide Stability summaries.

Possible descriptive summaries include Resonant, Stable, Strained, Fractured,
and Paradoxical. Initially these labels need not add a separate global rule,
although cards may refer to them.

### Directional scopes

Adjacency rules distinguish three structural sets:

- **Peer:** neighboring Lands in the same ring;
- **Inward or supporting:** relationship toward the Plane Seed;
- **Outward or supported by:** relationship toward later expansion.

Rules may address one set, any union of sets, all local relationships, an
entire ring, or a radial chain.

A regular hex ring does not give every tile identical inward and outward
neighbor counts. Corner tiles generally have one inward and three outward
geometric neighbors, while other positions may have two inward and two
outward neighbors. The final construction model may define a canonical inward
parent and outward children if uniform support language proves clearer. The
exact mapping remains open, but it must be deterministic and visible.

### Printed exceptions and build-around abilities

Examples include:

- “Does not suffer adjacency penalties.”
- “Halve adjacency penalties and double adjacency bonuses from Lands
  supporting this.”
- “Fire Lands supported by this have 1 less Essence upkeep.”
- “Opposed Peer affinities provide bonuses instead of penalties.”
- “Gain Stability for each distinct affinity among outward neighbors.”
- “Double all local adjacency effects, including penalties.”

Such text may ignore, halve, double, redirect, invert, cap, or deliberately
exploit normal Stability rules. Instability should support viable archetypes
rather than functioning only as failure.

## Economic Operations Pile

The Economic Operations Pile is an ordered pile of recurring economic cards.
It represents the Plane's organized undertakings while preserving visible
card-game sequencing.

Possible Operations include Harvest, Caravan, Forge Arms, Conduct a Survey,
Hold Market, Collect Tribute, Distill Mana, Train the Watch, Repair the Wards,
and Perform Seasonal Rites.

### Resolution rule

Only the top card may be evaluated.

It activates when:

- its cooldown has expired;
- its resource costs can be paid;
- every printed requirement is satisfied.

On activation:

1. pay its costs;
2. resolve its effects;
3. place it on cooldown;
4. move it to the bottom of the pile;
5. evaluate the new top card.

If the top card cannot activate, the entire pile waits. The simulator does not
skip, suspend, reserve for, or reorder it automatically.

### Blocking is a build rule

An unaffordable card at the top is a build flaw to be managed by the player.
The solution is to change pile order or composition, improve production, wait
for resources, or accept the stall.

A cooling-down card that returns to the top also blocks the pile. Players must
balance card count, production cadence, costs, cooldown length, and order so
the engine completes a useful cycle.

Deployed Operation cooldowns and readiness use the containing Plane's local
time. Advancing that Plane's time advances the pile, its costs, triggers, and
cooldowns together.

The interface must clearly identify the top card and the exact blocking
condition.

### Sequential execution and additional piles

Cards within one pile never execute in parallel. Exceptionally rare cards may
grant a second independent Operations Pile. Each pile remains internally
sequential and has its own top card and blocking state.

This exception should be rare because another pile changes the architecture of
the economy rather than merely increasing output.

Pile capacity, starting size, and card effects that modify size or cooldown
remain open design work.

### Lazy resolution

Operations do not require a continuous server tick. When the Plane is touched,
the simulator reconstructs chronological activity from the last stored state:

1. find when the current top card first became ready and affordable;
2. resolve it at that simulated time;
3. update resources, cooldown, and pile order;
4. evaluate the next top card;
5. stop at the present or at the first blocker.

Several Operations may have completed while the player was away, but their
effects always resolve in deterministic sequential order.

## Resource tiers

The exact resource list remains provisional. Tier indicates economic depth and
production requirements rather than quality or card rarity.

### Tier I — Natural or foundational materials

Examples include Materials, Metal, Organics, Wealth, Timber, Stone, Clay,
Herbs, Iron Ore, Coal, Gold Ore, and Uncut Gems.

### Tier II — Refined or prepared goods

Examples include Building Materials, Lumber, Masonry, Steel, Glass, Tools,
Arms, Provisions, and Medicine.

### Tier III — Magical reagents and materials

Examples include Mana Crystals, Arcane Dust, Spirit Residue, Living Wood, and
Elemental Reagents.

### Tier IV — Planar materials

Examples include Condensed Aether, Riftglass, Planar Alloy, and Stabilized
Essence.

### Tier V — Mythic resources

Examples include World Essence, Phoenix Ash, Celestial Amber, Infernal Seals,
Void Pearls, and Seeds of Eternity. These should carry particular rules and
narrative meaning rather than being merely expensive commodities.

### Canonical families and generated variants

Generated materials may retain fantasy specificity while satisfying broad
recipe requirements:

```text
Emberpine
Resource family: Materials / Timber
Tags: Organic, Fire, Primal
```

Grave-Iron may satisfy Metal, Shadow, and Death requirements. Dreamsilk may
satisfy Organics, Incorporeal, and Wandering requirements. Ordinary recipes
use broad families; specialized cards care about tags or exact variants.

## Per-resource storage

Capacity is tracked independently for every resource:

```text
stored amount / capacity for this resource
```

There is no shared warehouse allocation and no storage-priority interface.

### Intrinsic storage

Provisional baseline storage for a normal Land is:

- 2 capacity for every Tier I resource;
- 2 capacity for every Tier II resource;
- 1 capacity for every Tier III resource;
- no Tier IV or Tier V capacity.

Better or specialized Lands may intrinsically contribute 1 capacity for every
Tier IV and Tier V resource. Dedicated storage cards may provide much larger
or tag-specific capacity.

Intrinsic storage is structural and normally remains while a Land is dormant.
A card such as a conjured vault may explicitly lose granted capacity while
dormant.

### Safe Storage

Safe Storage is a protected subset of per-resource capacity. The protected
amount is automatic; players do not assign resources or priorities.

If a Plane stores 6 Gold, has capacity for 10 Gold, and has 4 Safe Gold
capacity, 4 Gold cannot be plundered and 2 Gold remain exposed.

A Secret Cave may grant modest Safe Storage across several tiers. A Hidden
Treasury may protect Wealth resources. An Arcane Vault may be required for
safe Tier IV storage. Exact card values remain procedural and balance-driven.

### At capacity

When a resource reaches capacity, further production of that resource stops.
Inputs should not be consumed for output that cannot be stored. Other
production continues normally, and the interface identifies the blocked
output.

## Exposed overflow

If construction changes reduce capacity below the stored amount, excess
resources are not silently destroyed. They become Exposed Overflow.

Overflow:

- remains available for spending;
- cannot increase through further production;
- receives no Safe Storage protection;
- is visible to the player;
- increases the Plane's attractiveness to opportunistic raiders.

The exact grace period or persistence rules remain open. The initial purpose is
to turn excess production into recoverable risk rather than immediate loss.

### AI smash-and-grab attacks

Generated factions, marauders, thieves, or opportunistic creatures may launch
occasional AI-controlled raids when exposed overflow is worth stealing. These
are objective-based attacks through the Plane's Rift and resolve against its
standing defense under the normal asynchronous combat foundation.

Their objective prioritizes exposed overflow. Success does not imply conquest
or permanent damage; attackers attempt to breach the required threshold, seize
what they can carry, and escape. Faction identity may determine preferred
resources, force composition, risk tolerance, and special events.

Raid opportunities must be generated deterministically during lazy simulation.
No background tick is required. The simulator derives eligible attempts from
the stored overflow state, elapsed time, Universe and faction state, and hidden
authoritative randomness, then resolves them in chronological order with
Operations and other Plane events.

Overflow should increase temptation rather than guarantee a raid or a loss.
Safe Storage, spending, added capacity, and a strong standing defense are all
valid responses.

## Open questions

- Final canonical resource families and generated-variant schema.
- Exact tier boundaries and whether some mythic resources are cards or tokens.
- Adjacency support mapping at ring corners and edges.
- Stability modifier curves and whether Plane-wide ratings gain default rules.
- Starting Operations Pile size and the rarity of additional piles.
- Cooldown, affordability, and chronological resolution details under large
  offline deltas.
- Whether reduced-capacity overflow expires and after what grace period.
- AI raid frequency, carrying limits, target selection, and faction generation.
- Exact intrinsic and Safe Storage values after balance testing.
