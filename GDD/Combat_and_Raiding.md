# Combat and Raiding

- **Status:** Foundational design; detailed resolution rules remain open
- **Related decisions:** [DD-0008](../Decisions/DD-0008-leaders-generals-and-force-construction.md), [DD-0009](../Decisions/DD-0009-asynchronous-objective-combat.md)
- **Related document:** [PlaneGuardian GDD](PlaneGuardian_GDD.md)

## Purpose

Combat allows players to attack, defend, harass, and plunder Planes through asynchronous forces assembled from their card collections. It should reward collection quality, synergy, planning, economic preparation, and timing without requiring either player to remain continuously online.

## The Rift

Every Plane Seed contains a Rift through which attackers, thieves, traders, and guests enter the Plane. Defense is organized around controlling this arrival point. The Plane Guardian configures a standing defensive force that can resolve attacks without live input.

## Card types and runtime roles

- **Creature:** one significant being or a small homogeneous creature presence.
- **Hero:** a specific individual.
- **Squad:** an organized group acting as one deployment.
- **Leader:** a capability that allows a qualifying card to command a force.
- **General:** the Leader assigned to a defensive army.
- **Expedition Commander:** the Leader assigned to an attacking force.
- **Army:** the complete configured force; it is not itself a card type.
- **Formation:** a deployment structure selected or unlocked by the commanding Leader; it is not initially a card type.

A large Creature may consume more command capacity than a Squad. Scale is therefore a deployment cost rather than a reason to make Army a card family.

## Force construction

Attack and defense use a shared planning structure:

```text
Army
  Commander
  Formation
  Tactical zones
    Front line
    Flanks
    Reserves
    Support
  Troop deployments
  Battle Events
  Source effects
```

The commanding Leader's type, affinities, quality, and abilities determine command capacity, favored or permitted troops, bonuses and penalties, formations, tactical zones, reserve capacity, and Battle Event support.

Quality influences command effectiveness. Complexity governs sophisticated formations, exceptions, triggers, and interactions. Rarity remains scarcity rather than a direct measure of power.

### Defensive capacity

```text
Defensive capacity =
  General command
  + Plane economy
  + defensive Lands and Facilities
  + persistent modifiers
```

A large, stable, wealthy Plane can sustain a larger standing defense. Capacity does not guarantee effectiveness: a small Plane with exceptional cards, synergy, and a strong General may defeat a larger force of poor cards.

### Attacking capacity

```text
Attacking capacity =
  Attack Action allowance
  + Expedition Commander modifiers
  + temporary modifiers
```

The Attack Action defines how large or specialized an expedition may be. The attacker's home economy may pay costs, but Plane size does not automatically determine attacking capacity.

## Battle Events

Battle Events may be deployed in timed zones or attached to troops with triggers such as entry, defeat, damage, movement, or a specified combat turn. They may represent spells, reinforcements, hazards, maneuvers, or other occurrences.

- **Deployed Battle Events** are selected by the player and enter cooldown after activation.
- **Generated Battle Events** are produced by another card, such as a Harpy Nest generating a Harpy attack on turn four. They inherit semantic identity and restrictions from their source and may exist only for that battle.

Generated names should preserve provenance. A Land named *The Galecliff Brood* might generate *Galecliff Harassment* rather than an unrelated event name.

## Attack Actions as engagement contracts

An attack requires an Action card and an Expedition Commander. The Action defines:

```text
Attack Action:
  objective
  attacking capacity
  permitted or favored troops
  objective threshold
  reward or consequence
  Action cooldown
  special rules
```

The Action's objective is separate from merely winning the battlefield exchange. **Breach** or **Objective Progress** measures whether the expedition accomplished its mission.

| Action archetype | Typical scale | Objective | Typical payoff |
| --- | --- | --- | --- |
| Probe | Very small | Reveal or test defenses | Information |
| Raid | Small | Reach a low threshold | Limited resources |
| Harassment | Small–medium | Defeat or disrupt defenders | Extended cooldowns |
| Sabotage | Specialized | Reach support or a Facility | Temporary impairment |
| Pillage | Large | Reach a high threshold | Significant plunder |
| Assault | Large | Defeat the defensive formation | Strategic advantage |
| Siege | Very large or persistent | Accumulate progress | Major Plane-level effect |

A Harassment attack may award no plunder while imposing double cooldown on defeated defenders, preparing the target for a later Pillage.

## Combat results

An attack produces three related results:

1. **Tactical result:** which force won the battlefield exchange.
2. **Attrition result:** which cards entered cooldown and for how long.
3. **Objective result:** whether the Action's threshold triggered its payload.

An attacker may lose tactically while inflicting useful attrition. An attacker may also win tactically but fail to achieve enough Objective Progress to earn plunder.

## Cooldown commitment

Defeated cards enter real-world cooldown. A card committed to a role cannot be exchanged while on cooldown. This applies to Action Deck slots, deployed defenders, Generals, Expedition Commanders, Battle Events, recovering attackers, and bound support cards as appropriate.

A defeated defender remains assigned to its tactical slot while recovering. The slot provides no active defender and cannot be filled from the collection until that card becomes ready. Collection depth provides configuration options but cannot erase attrition by cycling fresh cards into wounded positions.

## Asynchronous resolution and online reaction

An attack snapshots the defensive configuration when declared. The defender cannot retroactively alter that battle. The standing plan, General, formation, tactical zones, reserves, timed events, and triggers resolve without the defender being online.

An online defender may inspect completed reports, rearrange ready cards, adjust available events, change future priorities, or counterattack. They may not replace or move committed cards on cooldown. Being online improves information and preparation for later attacks but does not erase previous losses.

Attacks against one Plane must be serialized deterministically so concurrent attackers do not all fight the same pre-attrition state. The exact queue and transaction model remains technical work.

## Action cadence and time fairness

The Action Deck should support different play rhythms:

- active players may select many short-cooldown, low-capacity Actions for frequent small raids and tactical reactions;
- occasional players may select long-cooldown, higher-capacity Actions with larger thresholds and payoff.

Balance should target comparable expected opportunity over real time. Active play grants flexibility and information rather than an overwhelming economic multiplier. Limited readiness banking for completed long cooldowns may be considered so occasional players do not lose most theoretical value by logging in late.

## Open questions

- Turn sequence, initiative, targeting, movement, and formation disruption.
- Exact command-capacity and deployment-cost models.
- General defeat and succession rules.
- Reserve behavior after a defender enters cooldown.
- Breach and Objective Progress calculation.
- Plunder caps, resource protection, and failure costs.
- Attack serialization, queues, and multi-player coordination.
- Cooldown durations, extensions, and diminishing returns.
- Counterplay against repeated Harassment followed by Pillage.
- Whether long-cooldown Actions bank readiness and to what limit.
