# First Plane Onboarding

- **Status:** Foundational flow; content and exact grants remain provisional
- **Related decision:** [DD-0019](../Decisions/DD-0019-java-platform-and-first-plane-flow.md)
- **Related documents:** [PlaneGuardian GDD](PlaneGuardian_GDD.md), [Visual Identity and Main Stage](../Art/Visual_Identity_and_Main_Stage.md), [Card Origins and Protected Discovery](../Procedural/Card_Origins_and_Protected_Discovery.md)

## Purpose

The first session should teach PlaneGuardian by making the central fantasy
happen visibly: a whisper awakens the Guardian, an empty Void reveals an
unsprouted Seed, fragments become cards through activation, the player's
choices give the new Plane direction, cards become islands, and a first
Leader answers the emerging world.

## Application flow

```text
Splash
  -> Loading
  -> Login or Account Creation
  -> Game Menu
  -> Main Stage
```

- **Splash:** immediate identity and startup confirmation.
- **Loading:** assets, shaders, procedural generators, local cache, and network
  initialization behind a Void and dormant Seed motif.
- **Login or Account Creation:** authentication before authoritative state.
- **Game Menu:** Universe and Era status, Plane selection, collection access,
  settings, and account functions.
- **Main Stage:** current Plane, construction, economy, defense, and Guardian
  intervention.

First-Plane onboarding unfolds inside the Main Stage rather than a detached
character-creation wizard.

## First Plane sequence

1. Present an empty dark Void.
2. Play the whisper: “Awaken, Guardian.”
3. Give a short account of the shattered multiverse and unstable fragments.
4. Reveal and entrust the unsprouted Planar Seed and its Rift.
5. Locate the first fragments as crystals.
6. Ask a short evocative semantic questionnaire.
7. Activate the located starter fragments into a coherent common collection.
8. Teach placement with the first Lands and visible affinity contribution.
9. Grant a special first-Leader fragment activation Action.
10. Realise a slightly higher-Quality Hero guaranteed to have Leader.
11. Introduce the next immediate Plane objective.

The sequence should remain brisk and revisitable. Narrative presentation must
not conceal the mechanical consequences of choices after they are made.

## Semantic questionnaire

Questions use setting language rather than exposed coordinates. Possible
themes include preserving or transforming, walls or roads, rite or instinct,
patient craft or magical shortcut, elemental imagery, and cosmic patronage or
independence.

Answers create a shared starter profile rather than one fixed class. Starter
cards receive related influences with enough variation to avoid a solved
single-theme deck.

The exact number, wording, reroll policy, and ability to preview consequences
remain open.

## Domain-separated starter generation

The server selects required starter families through a versioned generation
context before deriving independent streams. It does not XOR or otherwise
mutate arbitrary bytes of a completed hash.

Conceptually:

```text
starterOrigin = HMAC(
  universeSecret,
  accountId,
  eraId,
  "starter",
  starterSlot,
  questionnaireProfile,
  generatorVersion
)
```

Independent streams derive:

```text
family
semantics
mechanics
name
art
```

The generation context may fix the family for a slot while the protected
origin determines the card within that family. A starter package may therefore
guarantee a Seed, Lands, a recurring-pile card, and an Action without weakening
the protected discovery mapping.

If future reconstruction requires family to be encoded in a standalone GUID,
versioned reserved type bits may be assigned before filling the remaining bits
cryptographically. Post-hash XOR is not the default design.

## First Leader activation

The special Action provisionally represents activating a fragment into the
Plane's first Warden. Inputs include:

- Planar Seed profile;
- questionnaire profile;
- starter collection semantics;
- dominant and secondary affinities;
- one controlled complementary or contrasting influence;
- account, Universe, Era, action, and generator domains.

The resulting Hero has:

- guaranteed Leader capability;
- slightly elevated Quality relative to ordinary starter commons;
- at least partial compatibility with available troops and Lands;
- a simple initial formation or command identity;
- enough imperfection to leave room for future collection growth.

The Action uses player-space Real Time. The exact supply, tradability, binding,
repeatability, and reroll protections remain open.

## First-session teaching goals

The player should leave onboarding understanding that:

- card identity is deterministic and meaningful;
- the Seed defines but does not completely dictate the Plane;
- Lands become ordered hex islands;
- affinities and adjacency matter;
- active extent depends on Astral Essence;
- the collection supplies multiple roles;
- the first Leader is shaped by the world being built.

Detailed economy, combat, attachment depth, and advanced procedural semantics
should arrive later.

## Open questions

- Exact starter card count and family guarantees.
- Questionnaire length, wording, visibility, and accessibility.
- Starter card supply, trading, deletion, and reroll prevention.
- Whether the first Leader is account-bound, Era-bound, or ordinarily tradable.
- Failure recovery if generation or account creation is interrupted.
- Whether experienced players may use an abbreviated onboarding in later Eras.
