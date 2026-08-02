# DD-0014 — Plane Economy Foundations

- **Status:** Accepted
- **Date:** 2026-08-01
- **Affected documents:** [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md), [Plane Economy and Operations](../Economy/Plane_Economy_and_Operations.md)

## Context

Plane construction, Astral Essence upkeep, spatial compatibility, recurring
economic actions, storage, and raiding need to form one legible card-game
engine. The economy should reward building small production chains without
forcing universal subsistence chores or deep low-tier manufacturing chains.

Automation must preserve player responsibility. An invalid economic sequence
should be a visible build flaw rather than something the simulator silently
skips or repairs.

## Decision

The foundational Plane economy uses these connected rules:

- **Static adjacency Stability:** all configured Lands contribute to visible
  bonuses and penalties, primarily modifying Astral Essence upkeep. Card text
  may alter or exploit those rules.
- **Ordered prefix activation:** Lands activate in list order until adjusted
  Essence upkeep can no longer be paid; remaining Lands become dormant.
- **Sequential Economic Operations Pile:** only the top card may activate. An
  unaffordable, ineligible, or cooling-down top card blocks the pile. A
  successful card resolves, enters cooldown, and moves to the bottom.
- **Exceptional parallel engines:** cards in one pile never resolve in
  parallel, but exceptionally rare effects may grant a second independent
  pile.
- **Per-resource storage:** capacity is tracked independently for every
  resource. Normal Lands provisionally contribute 2 capacity per Tier I and
  Tier II resource and 1 per Tier III resource. Tier IV and Tier V normally
  require better or specialized Lands.
- **Safe Storage:** automatically protects an amount of each resource and does
  not require player-managed priorities.
- **Exposed overflow:** resources above reduced capacity remain temporarily
  exposed rather than disappearing. They cannot increase and are vulnerable to
  plunder, including deterministic AI smash-and-grab attacks.

Routine food, maintenance, and similar needs are assumed unless making them
explicit creates a distinctive decision or card identity.

## Rationale

These rules make layout, Land order, and Operations order three different but
interacting card-game decisions. Stability uses the existing Essence economy
instead of introducing a redundant activation currency. Blocking Operations
make sequencing and cooldown cadence meaningful. Per-resource storage removes
allocation chores, while overflow turns excess production into visible risk
and emergent encounters rather than silent waste.

## Consequences

- The builder must preview local adjacency modifiers, final upkeep, and active
  extent before changes are committed.
- Dormant Lands normally retain structural storage so Essence loss does not
  cause an immediate destructive storage cascade.
- Lazy simulation must replay Operations and AI overflow raids in deterministic
  chronological order when the Plane is touched.
- Resource design should favor broad requirements, substitution, distinctive
  appetites, and short routine chains.
- Exact resource names, storage quantities, overflow duration, AI raid
  frequency, and geometric support mapping remain subject to balancing and
  implementation testing.
