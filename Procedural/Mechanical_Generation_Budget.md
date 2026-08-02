# Mechanical Generation Budget

- **Status:** Foundational mathematical model; constants remain provisional
- **Related decision:** [DD-0016](../Decisions/DD-0016-mechanical-generation-budget.md)
- **Related documents:** [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md), [Plane Economy and Operations](../Economy/Plane_Economy_and_Operations.md), [Lore Map and Affinity Wheels](Lore_Map_and_Affinity_Wheels.md)

## Purpose

Mechanical generation needs a common value language for production, costs,
storage, slots, capacities, triggers, conditions, and disadvantages. The model
must reward production chains without producing free budget or closed-loop
resource amplification.

## Generic Land chassis

The generic Land defines the mechanical zero point:

```text
Semantic profile:
  contributes its affinities to the Plane

Biome or Land type:
  selects a compatible ordinary resource

Production:
  1 Tier I resource per Plane Day

Storage:
  baseline lower-tier capacity

Upkeep:
  standard Land Astral Essence upkeep

Attachments and abilities:
  none
```

The chassis is the baseline entitlement for a Land. Its generated budgets buy
properties above that baseline.

## Ability Value Unit

One **Ability Value Unit (AVU)** is the expected value of producing one
additional Tier I resource per Plane Day at full uptime under reference
conditions.

AVU is a hidden design and generator measure, not necessarily a player-facing
stat. It allows unlike features to be compared after testing and expected-value
conversion.

Examples of features that require AVU valuation include additional production,
higher-tier output, Essence upkeep, attachment slots, Safe Storage, defense or
recurring-pile capacity, adjacency, triggers, eligibility, and cooldowns.

## Resource reference values

Tier I has reference value 1 per unit. Higher tiers receive versioned constants
based on expected production depth, restrictions, and utility:

```text
RESOURCE_VALUE_T1 = 1
RESOURCE_VALUE_T2 = TBD
RESOURCE_VALUE_T3 = TBD
RESOURCE_VALUE_T4 = TBD
RESOURCE_VALUE_T5 = usually non-fungible or card-specific
```

Tier V may not admit one ordinary exchange value because its resources can
carry unique rules and Era-level meaning.

## Production and conversion

For a continuous recipe under reference conditions:

```text
netEconomicValue = outputReferenceValue - inputReferenceValue
```

The card's Power budget pays for positive net economic value. This margin is
the dividend that rewards the player for supplying inputs, Essence, a card or
attachment slot, storage, and dependency management.

If Tier II is illustratively valued at 2, then consuming 1 Tier I to produce 1
Tier II creates net value 1 and costs approximately 1 AVU before other factors.
Consuming 1 Tier I to produce 2 Tier I also creates net value 1, but requires
additional loop validation.

Inputs do not grant two or three times their value as generation credit. Doing
so would let a card gain net production and spare ability budget merely by
adding an easily supplied input.

## Input and downside credit

An initial conceptual model is:

```text
credit = magnitude
       * expectedFrequency
       * coupling
       * enforceability
       * rebateFactor
```

- **Magnitude:** cost when the disadvantage occurs.
- **Expected frequency:** occurrence under reference play.
- **Coupling:** how reliably the cost accompanies the funded benefit.
- **Enforceability:** how difficult it is to bypass while retaining the
  benefit.
- **Rebate factor:** intentional discount that keeps disadvantages from
  becoming a superior source of power.

Consumed resource credit does not exceed consumed reference value. Optional,
controllable, narrow, or easily avoided disadvantages receive less.

Generated downsides may include higher upkeep, resource inputs, adjacency
penalties, storage loss, periodic dormancy, cooldown extension, vulnerability,
eligibility restrictions, or triggered hazards.

## Lossy rebates and caps

Equivalent negative and positive text need not have symmetric prices. A
positive effect costing 1 AVU may refund less than 1 AVU when inverted into a
controllable downside.

Downside-funded additional positive power is capped as a proportion of the
card's original Power budget. Exact rebate factors and caps remain constants
for simulation and balance testing. Exceptional cards may receive larger
limits through explicit generation rules and Complexity cost.

## Separate budgets

### Power Budget

Measures expected mechanical advantage in AVU under reference conditions.

### Complexity Budget

Limits rules machinery such as triggers, targets, branches, relationships,
exceptions, generated Events, transformations, secondary outputs, attachment
depth, and multiple semantic tensions.

A powerful simple card and a modest intricate card can therefore both exist.
Rarity remains scarcity rather than raw power. Quality, Efficiency, and
Complexity still require exact mathematical relationships to available and
realized Power budget.

## Land generation outline

1. Generate the semantic profile.
2. Select a compatible biome and baseline Tier I output.
3. Apply generic storage and standard upkeep.
4. Generate Power and Complexity budgets.
5. Consider additional tags and global capacities.
6. Consider an Enhancement slot using provisional occurrence rates.
7. Buy production, storage, adjacency, eligibility, triggers, and abilities.
8. Optionally generate disadvantages and calculate discounted credit.
9. Spend permitted credit without exceeding downside-funded power caps.
10. Validate loops, contradictions, usability, and power ceilings.
11. Produce final Efficiency and presentation data.

## Validation requirements

Generation validators should test closed production loops, same-resource
amplification, costs that can be disabled without losing their benefit,
impossible requirements, attachment or Event recursion, time-rate feedback,
unbounded downside-funded power, and combinations whose realized value greatly
exceeds reference estimates.

## Constants to establish

The eventual versioned constant set includes tier reference values, base Land
upkeep and storage, slot cost and burden, Essence-to-AVU conversion, expected
uptime, downside factors and caps, trigger frequencies, capacity values,
Quality and Efficiency curves, and validation ceilings.

## Open questions

- Reference environment and expected collection maturity.
- Exact Tier II–IV economic values.
- Whether resource families within one tier have value modifiers.
- Essence's AVU conversion and the value of activation-order risk.
- Slot and Plane-wide capacity valuation.
- Quality, Efficiency, rarity, and Complexity relationships.
- Whether AVU is stored directly or compiled into fixed-point generator units.
- Automated search and simulation methods for exploit detection.
