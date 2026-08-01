# DD-0004 — Universes, Eras, and Eternal Cards

- **Status:** Accepted
- **Date:** 2026-08-01
- **Affected documents:** [Card Origins and Protected Discovery](../Procedural/Card_Origins_and_Protected_Discovery.md), [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md)

## Context

PlaneGuardian needs periodic renewal without making past play meaningless. Multiple Universes should support distinct card spaces, while some exceptional cards should accumulate history across resets.

## Decision

A Universe is a persistent historical lineage, and an Era is a reset cycle within it. Protected generation context includes immutable Universe, Era, and generator-version identifiers. Completed Eras become read-only history in a Hall of Fame.

Eternal is a lifecycle axis separate from rarity and quality. Eternal cards retain identity and provenance across Eras but receive no promotion bonus. They reside in an Eternal Vault and are subject to limited activation in future Eras. Cards may be Born Eternal, Ascended, Consecrated, or Honored within a published Eternal Budget.

## Rationale

- Give seasonal resets an in-world meaning.
- Preserve accomplishments without preserving the entire active economy.
- Allow historical cards to become genuine artifacts.
- Prevent accumulated Eternal collections from invalidating fresh starts.

## Consequences

- Reset boundaries and Eternal activation limits require explicit balance rules.
- Generator versions needed by Eternal cards must remain available.
- Promotion records are immutable and cannot alter card mechanics.
- Universe display names are flavor, not cryptographic key material.
