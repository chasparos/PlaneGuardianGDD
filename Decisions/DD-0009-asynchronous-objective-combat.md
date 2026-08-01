# DD-0009 — Asynchronous Objective Combat

- **Status:** Accepted
- **Date:** 2026-08-01
- **Affected documents:** [Combat and Raiding](../GDD/Combat_and_Raiding.md), [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md)

## Context

Combat must support meaningful attack, defense, attrition, and different player schedules without requiring the defender to be online or allowing continuous presence to erase losses.

## Decision

Every Plane Seed contains a Rift defended by a configured standing army. An Attack Action acts as an engagement contract defining force allowance, objective threshold, payoff or consequence, cooldown, and special rules. Tactical victory, attrition, and objective completion are separate results.

Combat snapshots the defense when an attack is declared and resolves asynchronously. Defeated cards enter cooldown. A deployed defender on cooldown remains committed to its slot and cannot be replaced until ready. The same commitment principle applies to other cards assigned to cooldown-governed roles.

Short-cooldown Actions support frequent small attacks; long-cooldown Actions support less frequent, higher-impact play. Balance targets comparable opportunity over real time while allowing active play to retain informational and tactical flexibility.

## Rationale

- Make standing defense viable for offline players.
- Let attacks pursue information, attrition, disruption, or plunder rather than one victory condition.
- Make cooldown a persistent commitment and strategic wound.
- Support both frequent and occasional play rhythms through Action Deck construction.

## Consequences

- Attack declaration must atomically snapshot defense and serialize attacks against a Plane.
- Online defenders may prepare for later attacks but cannot alter a battle already declared or replace recovering cards.
- Harassment can prepare a target for Pillage, creating coordinated attrition strategies.
- Detailed battle turns, Breach calculation, cooldown balance, and anti-abuse counterplay remain open.
