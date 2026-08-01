# DD-0008 — Leaders, Generals, and Force Construction

- **Status:** Accepted
- **Date:** 2026-08-01
- **Affected documents:** [Combat and Raiding](../GDD/Combat_and_Raiding.md), [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md)

## Context

Attack and defense require a commander, troops, formation, tactical deployment, and support. Treating Leader, General, Formation, and Army as independent card families would blur the distinction between permanent cards and configured combat roles.

## Decision

Leader is a capability that permits a qualifying card to command a force. A Leader assigned to defense is the General; a Leader assigned to attack is the Expedition Commander. Army and Formation are configured combat structures rather than initial card types.

The commander influences command capacity, eligible or favored troops, bonuses, formations, tactical zones, reserves, and Battle Event support. A Plane's economy supports defensive capacity, while an Attack Action defines the attacking force allowance. Capacity controls deployment size but does not replace card quality, synergy, or tactical planning.

## Rationale

- Use one force-planning model for attack and defense.
- Allow several entity families to produce Leaders without duplicating card types.
- Let wealthy Planes sustain broader defenses while elite small defenses remain viable.
- Keep Rarity separate from direct command power.

## Consequences

- General and Expedition Commander are assignments with mutable state.
- Quality and Complexity require distinct command effects.
- Troop deployment costs and command-capacity formulas remain open.
- Army names describe configured forces rather than permanent card identities.
