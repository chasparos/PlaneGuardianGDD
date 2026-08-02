# DD-0017 — Clock Ownership and Timeless Combat

- **Status:** Accepted
- **Date:** 2026-08-02
- **Affected documents:** [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md), [Time, Combat, and Cross-Plane Effects](../GDD/Time_Combat_and_Cross_Plane_Effects.md), [Combat and Raiding](../GDD/Combat_and_Raiding.md)

## Context

Individual Planes may experience different local time rates, while the
Guardian's Action Deck must preserve fair real-world cadence. Moving cards
between Planes would introduce foreign clock ownership, travel simulation, and
complex synchronization without being central to the game.

## Decision

Every timed state has a clock owner:

- deployed cards, attachments, local Events, healing, production, and the
  recurring Operations pile use their containing Plane's local time;
- the Guardian's player-space Action Deck and account-level systems use
  authoritative Real Time;
- explicit Plane-time advancement resolves all local production, consumption,
  upkeep, cooldowns, healing, Operations, Events, storage, overflow, and
  hazards through the advanced interval;
- combat consumes no elapsed time in either Plane. Battle turns are ordered
  resolution steps rather than time units;
- participating cards do not travel to or persist within another Plane;
- persistent cross-Plane consequences are spawned runtime Effects attached to
  the target and governed by the target Plane's time.

By default, a spawned Effect snapshots its mechanical payload on creation and
retains its source reference for provenance. Explicit text may instead make it
source-bound or sustained.

## Rationale

The rule matches the fiction that deployed things experience their Plane while
keeping player intervention on a common real-world cadence. Timeless combat
removes travel and clock-conversion complexity. Target-local Effects preserve
rich curses, blessings, sabotage, and marks without transferring owned cards.

## Consequences

- A time-advance Action progresses both opportunities and consequences inside
  the target Plane but not its own Real-Time cooldown.
- Defeated attackers recover on their home Plane's time; defenders recover on
  the defended Plane's time.
- Attacks remain authoritatively serialized even when they share one displayed
  Plane timestamp.
- Spawned Effects are runtime objects rather than owned collection copies.
- Exact individual Plane-time rates, combat transaction ordering, Effect
  dispelling, and clock rules for future delegated Actions remain open.
