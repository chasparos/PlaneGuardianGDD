# DD-0015 — Card Zones, Attachments, and Commitment

- **Status:** Accepted
- **Date:** 2026-08-02
- **Affected documents:** [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md), [Card Zones and Attachments](../GDD/Card_Zones_and_Attachments.md), [Plane Economy and Operations](../Economy/Plane_Economy_and_Operations.md)

## Context

The collection contains Lands, entities, persistent modifications, Actions,
Events, Relics, and recurring economic cards. Their deployment grammar must be
clear without filling procedural collections with narrow incompatibilities.
Local attachment capacity must also remain distinct from Plane-wide budgets
and eligibility granted by Lands.

## Decision

Only Land cards create ordinary hex tiles around the Planar Seed. Other cards
occupy explicit Plane or player-space zones, attach through broadly typed host
slots, or contribute through configured forces and piles.

Structure, Facility, Enchantment, Location, Fortification, and similar ideas
are normally Enhancement subtypes or tags rather than separate top-level
deployment families. Creature, Hero, and Squad are Entity subtypes. Exact
player-facing family names remain provisional.

Approximately 20% of generated Lands provisionally receive one Enhancement
slot and 0.1% receive two. A slot consumes generation budget and normally
increases Land upkeep even while empty. An attached card adds its own upkeep.
Slotless Lands retain budget for intrinsic production, adjacency, capacity,
eligibility, or abilities.

Hard compatibility constraints are rare and broad. Most semantic tension is
expressed through upkeep, Stability, bonuses, penalties, and printed synergy.
Cards may host other cards only through explicit broadly typed slots. Nested
attachments are permitted by the architecture but gain rapidly increasing
upkeep and Complexity costs.

Each owned card copy is a distinct instance and may occupy only one committed
role at a time. Owning multiple copies permits multiple deployments where all
other rules allow.

## Rationale

This model preserves a clear ordered Land UI and keeps the large procedural
card space usable. Soft compatibility makes imperfect combinations playable,
while slots and global budgets create meaningful opportunity costs. Instance
commitment ensures collection depth matters without allowing one rare card to
serve every role simultaneously.

## Consequences

- Lands may grant Rift defense, Battle Event, recurring-pile, troop
  eligibility, and other Plane-wide capacities without having local slots.
- Equipment on entities and Enhancements on Lands are normal pairings, while
  unusual pairings require explicit host slots such as Domain, Baron, or
  Instructor.
- The same Land instance cannot be both a terrain hex and a General's attached
  Domain.
- Removing, replacing, cooling down, and nesting attached cards require later
  lifecycle and UI rules.
- Automated player-space Actions remain a possible future explicit deployment
  exception rather than a default capability.
