# Time, Combat, and Cross-Plane Effects

- **Status:** Foundational design; exact rates and transactions remain open
- **Related decision:** [DD-0017](../Decisions/DD-0017-clock-ownership-and-timeless-combat.md)
- **Related documents:** [PlaneGuardian GDD](PlaneGuardian_GDD.md), [Combat and Raiding](Combat_and_Raiding.md), [Plane Economy and Operations](../Economy/Plane_Economy_and_Operations.md)

## Purpose

Clock ownership determines which elapsed time advances a card or Effect. The
model should support individual Plane time rates and complete offline
evaluation without simulating travel between Planes.

## Clock domains

### Plane Time

Plane Time governs state deployed inside one Plane:

- production and consumption;
- Astral Essence upkeep;
- Lands and Enhancements;
- the recurring Operations pile;
- deployed cooldowns;
- healing and recovery;
- local Events and seasons;
- construction and refinement;
- standing defenders;
- attached runtime Effects;
- local hazards, overflow, and raid opportunities.

### Real Time

Authoritative Real Time governs the Guardian's external player space:

- Action Deck cooldowns;
- account-level discovery restrictions;
- matchmaking and social restrictions;
- Era and server schedules;
- other explicitly account-owned systems.

The default follows zone ownership rather than an arbitrary label on each
mechanic.

## Plane-time rate

Conceptually:

```text
planeDelta = realDelta * planeTimeRate + explicitPlaneTimeAdvance
```

The exact baseline relationship remains open. A Plane's Seed, cards, Stability,
Events, or hostile Effects may alter its rate. Faster time advances both
opportunity and consequence: production, inputs, upkeep, healing, cooldowns,
Operations, hazards, and overflow exposure all progress together.

## Complete time advancement

An Action such as “advance the target Plane by one Plane Week” runs a genuine
week of local history. It does not merely multiply current production.

The lazy simulator advances chronologically to each relevant event, resolves
state changes, schedules resulting events, and continues until the target
Plane timestamp. A blocked Operation, depleted input, dormancy transition,
storage cap, triggered Event, or raid can alter everything that follows.

The Action remains in player space, so its own cooldown uses Real Time and is
not shortened by the Plane advancement it causes.

## Timestamp representation

Deployed cooldowns should normally store a target local timestamp:

```text
readyAtPlaneTime = currentPlaneTime + cooldownDuration
```

Player-space Actions store an authoritative Real-Time readiness timestamp.
The simulator compares timestamps rather than decrementing every card
continuously.

## Combat outside elapsed time

Combat has turns and ordered triggers, but those are resolution steps rather
than time durations. During combat:

- neither Plane produces or consumes resources through elapsed time;
- Operations do not progress;
- healing and deployed cooldowns do not advance;
- seasons and ordinary timed Plane Events do not progress;
- participating cards do not spend time away from home.

The Rift, attack Action, or other narrative mechanism may create an
interstitial or suspended battlefield. Exact cosmological explanation remains
lore work.

Combat is an atomic state transition that can still produce cooldowns,
plunder, attached Effects, revealed information, objective progress, and
reports.

## No cross-Plane card travel

Attacking cards retain their home Plane and participate through combat
representations rather than relocated owned instances. After resolution:

- defeated attackers receive cooldowns on their home Plane's clock;
- defenders receive cooldowns on the defended Plane's clock;
- surviving cards retain their home assignments;
- the initiating Action receives its Real-Time cooldown;
- no journey or foreign residency is simulated.

The foundational rule is:

> Cross-Plane interactions transfer consequences, not cards.

## Spawned runtime Effects

A persistent remote consequence creates an Effect attached to a target. The
Effect is not an owned collection card and does not consume another copy from
global supply.

Example:

```text
Cursed!

Source:
  The Ash-Tongued Maledictor

Target:
  Hero instance

Duration:
  1 target Plane Week

Effect:
  This Hero takes double damage.
```

Its expiry is expressed in target-local time:

```text
expiresAt = targetPlaneTime + 1 Plane Week
```

Advancing the source Plane does not progress the curse.

## Effect payload and provenance

The default Effect records:

```text
sourceCardId
sourceAbilityId
targetId
createdAtTargetPlaneTime
expiresAtTargetPlaneTime
snapshottedPayload
tags
tetherMode
```

The source reference preserves naming, visual identity, lore, reports, and
explicit interactions. Mechanical values are normally snapshotted so an
existing Effect does not silently change when its source is modified.

Possible explicit tether modes include:

- **Independent:** persists regardless of later source state;
- **Source-bound:** ends when its source leaves a required deployment;
- **Sustained:** continually depends on a printed source condition.

Independent is the default.

## Effect attachment scopes

Effects may attach to one card instance, an attachment stack, a Land, a ring or
radial region, the Rift defense, the recurring Operations pile, one resource
family, or the entire Plane. Target scope determines what the Effect can modify
and which Plane owns its clock.

## Authoritative ordering

Timeless does not mean simultaneous. Attacks and other cross-Plane state
changes are serialized by an authoritative sequence. A later attack observes
cooldowns, plunder, and Effects produced by earlier attacks even if both share
one displayed Plane timestamp.

Lazy simulation must merge target-local timed events and timeless externally
submitted transactions deterministically. Exact transaction and tie-breaking
rules remain technical work.

## Clock ownership summary

| Object | Clock owner |
| --- | --- |
| Action in Guardian player space | Real Time |
| Deployed Land or Enhancement | Containing Plane |
| Recurring Operation | Containing Plane |
| Standing defender | Defended Plane |
| Attacking card after combat | Home Plane |
| Battle | No elapsed time |
| Battle turn | Ordinal step |
| Remote attached Effect | Target Plane |
| Account or Era system | Real Time |

## Open questions

- Baseline Plane-time rate and allowed rate ranges.
- Effects of changing time rate during a large offline delta.
- Event ordering at identical local timestamps.
- Combat transaction serialization and rollback behavior.
- Dispel, cleanse, replacement, and stacking rules for runtime Effects.
- Whether any future voluntary transfer system should exist outside combat.
- Clock ownership for future delegated or automated Actions.
