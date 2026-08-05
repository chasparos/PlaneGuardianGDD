# Card Origins and Protected Discovery

- **Status:** Foundational design
- **Related decisions:** [DD-0003](../Decisions/DD-0003-protected-source-discovery.md), [DD-0004](../Decisions/DD-0004-universes-eras-and-eternal-cards.md)
- **Related document:** [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md)

## Purpose

Players locate fragments of reality by supplying a meaningful or arbitrary
lead, such as a location, divination, crafted formula, quest prompt, or free
text. A lead may also be phrased as an intention or incantation, but finding a
fragment is not the same event as realising its card.

The mapping must not permit players or bots to enumerate billions of candidate phrases offline in search of optimal cards.

## Origin pipeline

```text
Player source
  -> canonical source
  -> protected source mapping
  -> Origin ID
  -> latent fragment claim
  -> activation process
  -> deterministic card definition
  -> realised-card supply claim
```

Source type is part of the mapping. The same words used as a location and as
an incantation may therefore resolve to different fragments.

Canonicalization should make intentional sharing practical while preventing invisible variants. The initial policy should include Unicode normalization, removal of control characters, surrounding whitespace removal, repeated-whitespace collapse, and invariant case folding. Whether punctuation is significant remains an implementation detail.

## Protected mapping

Card mechanics remain reconstructable from the resulting Origin ID, as required by DD-0001. The mapping from player text to that identifier is server-controlled:

```text
OriginID = HMAC(EraKey, SourceType + CanonicalSource)
```

The server-held key prevents offline source mining. Discovery attempts also consume an in-game action, cost, or cooldown so online enumeration remains costly and observable.

## Supply claims

Card definition and card supply are separate. The supply ledger records:

- maximum global copies;
- issued copies;
- per-account limit;
- numbered copy identities;
- discovery and ownership provenance.

A discovery claim atomically resolves the source and records the latent
fragment. Activation then resolves the card, enforces the account limit and
global supply, issues the realised copy, and records the activation event.
These operations may be combined for a simple Action, but the design must
retain the conceptual distinction and must never let activation bypass supply
limits. Once a unique fragment or realised card has been claimed, later
seekers may learn that the source was claimed but cannot receive another copy.

Leads are shareable knowledge. A player who finds a desirable limited
fragment may deliberately share its source with friends or guild members,
creating exploration rumors and limited magical gold rushes.

## Universes and Eras

A Universe is a persistent historical lineage with an immutable internal identifier, a display name, and a protected root key. An Era is a reset cycle within that Universe.

```text
EraKey = DeriveKey(
  UniverseSecret,
  UniverseID,
  EraID,
  GeneratorVersion
)
```

The same source remains stable during an Era but may reveal a different card in another Era or Universe. Universe display names may influence flavor but must not act as security keys.

An Era progresses conceptually through Awakening, Expansion, Convergence, Reckoning, and Memory. At Reckoning, results are locked and the Era becomes read-only history in a Hall of Fame.

## Temporal, Legacy, and Eternal persistence

- **Temporal** state is reset or archived at the end of an Era.
- **Legacy** state remains visible as history but is not mechanically active.
- **Eternal** cards remain owned and may be activated in later Eras.

Eternal is a lifecycle axis independent of rarity and quality. Eternity preserves identity, not power. Promotion does not reroll or strengthen a card.

An Eternal card preserves its Origin ID, generator version, mechanics, provenance, approved player name and art, and history across Eras. Eternal cards reside in an Eternal Vault; only a limited number may awaken in an active Era, possibly after an opening grace period or by paying Era-specific costs.

## Paths to Eternity

- **Born Eternal:** determined procedurally and exceptionally rare.
- **Ascended:** preserved through a limited end-of-Era achievement or choice.
- **Consecrated:** preserved through an expensive collaborative ritual.
- **Honored:** selected for extraordinary historical or community-recognized significance.

Each Era has a published Eternal Budget. Promotion occurs only after final results are locked, does not change mechanics, cannot be repeated, and records an immutable reason and provenance.

## Hall of Fame

Completed Eras should preserve final Planes, major discoveries, discoverers and creators, guild accomplishments, notable conflicts, economic records, approved art and names, and cards born or promoted Eternal.

The server may publish a cryptographic commitment to an Era key at its beginning and reveal the retired key after claims close. This would enable community verification without permitting live-Era mining. Whether retired keys are revealed remains open because disclosure also removes some mystery.

## Open questions

- Exact source types and canonicalization rules.
- Online enumeration controls and discovery costs.
- Per-rarity supply ranges and account limits.
- Eternal Budget size and activation-slot progression.
- Exact reset boundaries for resources, Planes, cooldowns, and progression.
- Whether retired Era keys are revealed for verification.
