# DD-0016 — Mechanical Generation Budget

- **Status:** Accepted
- **Date:** 2026-08-02
- **Affected documents:** [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md), [Mechanical Generation Budget](../Procedural/Mechanical_Generation_Budget.md), [Plane Economy and Operations](../Economy/Plane_Economy_and_Operations.md)

## Context

Procedurally generated cards need a common value model so production,
consumption, storage, slots, triggers, capacities, and disadvantages can be
balanced coherently. Conversion chains should reward construction without
allowing input costs to manufacture free generation budget or arbitrage loops.

## Decision

The generic Land is the baseline chassis. It contributes its Lore Map profile,
has a biome-derived Tier I output, produces 1 unit per Plane Day, supplies
baseline lower-tier storage, pays standard Essence upkeep, and has no slot or
additional ability.

One **Ability Value Unit (AVU)** equals the expected value of producing one
additional Tier I resource per Plane Day at full uptime under reference
conditions. Positive abilities and disadvantages are translated into AVU for
generation and balance testing.

Resource conversion is valued by output reference value minus input reference
value. Consumed input grants no more budget credit than its own reference
value; controllable or avoidable costs normally receive discounted credit.
The generated card spends positive Power budget on the conversion margin that
rewards the player.

Power Budget and Complexity Budget remain separate. Downsides may release
discounted Power budget, but downside-funded power is capped and all generated
cards require loop, exploit, usability, and power-ceiling validation.

## Rationale

AVU supplies a common ruler without pretending every mechanic is literally a
resource. Paying for net value allows useful refining chains while preventing
“consume one” from granting multiple free budget units. Lossy rebates keep
clean cards competitive with cards whose nominal disadvantages are easy to
avoid.

## Consequences

- Tier I has reference value 1 AVU per unit per Plane Day; higher-tier values
  remain balance constants to be determined.
- Expected frequency, coupling, enforceability, and magnitude affect downside
  credit.
- A conversion from value 1 to value 2 provides a player dividend of 1 and
  costs the card approximately 1 AVU before other modifiers.
- Quality, Efficiency, Complexity, rarity, and base Power budget still need
  exact mathematical relationships.
- Reference environments and automated generation validators become necessary
  implementation tools.
