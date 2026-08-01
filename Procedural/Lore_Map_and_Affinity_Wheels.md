# Lore Map and Affinity Wheels

- **Status:** Foundational design
- **Related decisions:** [DD-0002](../Decisions/DD-0002-semantic-lore-map.md)
- **Related document:** [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md)

## Purpose

PlaneGuardian must generate mechanics, names, art, and lore that feel as if they describe the same artifact. The Lore Map provides a shared semantic model so individual generators do not make unrelated random choices.

The system should prevent accidental nonsense without eliminating deliberate paradox. A fire-and-ice entity, benevolent infernal being, or life-giving embodiment of death may exist when the card's complexity and relationships explain the tension. Contradictions are authored procedural events, not random collisions.

## Lore Map

The Lore Map is a versioned semantic graph. Its nodes represent concepts, while its edges describe relationships such as:

- affinity;
- opposition;
- compatibility;
- tension;
- prerequisite;
- transformation;
- cultural association;
- semantic distance.

Not every concept must be forced onto a circular wheel. The overall system may use:

- **wheels** for cyclic or directional relationships;
- **axes** for direct oppositions;
- **graphs** for irregular relationships such as cultures, creature families, and resources;
- **hard constraints** where a generated property requires or excludes another property.

## Initial affinity wheels

Version 0.1 begins with six semantic families. Their exact sectors, vocabulary, and probability distributions remain future work.

### 1. Elemental Affinity

Represents elemental identity and relationships. It may influence damage, resistance, resource production and consumption, environment, art, abilities, and naming.

### 2. Ethos

Uses two axes:

```text
Order <-> Chaos
Life  <-> Death
```

Life is not inherently good, and Death is not inherently evil. Example regions include ordered cultivation, wild adaptation, funerary inevitability, and entropic decay.

### 3. World Relation

Uses two axes:

```text
Preservation <-> Transformation
Creation     <-> Annihilation
```

This wheel describes how a card relates to existence and change. Its regions include restoration, invention, purification through sacrifice, and dissolution. Destruction may appear as a process within Transformation; Annihilation means erasure rather than ordinary damage.

### 4. Cosmic Provenance

Uses the axis:

```text
Divine <-> Infernal
```

This describes provenance, not morality. Divine beings may be tyrannical, while Infernal beings may be honorable or protective. Mortal, natural, arcane, or unaligned concepts occupy the center. A future second axis such as Covenant–Sovereignty may be added if testing shows that the single axis is insufficient.

### 5. Magical Tradition

Uses two axes:

```text
Arcane     <-> Primal
Controlled <-> Instinctive
```

This distinguishes calculated wizardry, structured primal ritual, instinctive sorcery, and untamed natural power.

### 6. Manifestation

Uses two axes:

```text
Material <-> Ethereal
Rooted   <-> Wandering
```

This distinguishes fortresses, mountains, shrines, hauntings, caravans, migrating creatures, dreams, and astral currents.

## Wheel coordinate model

Every applicable wheel produces a deterministic coordinate. A two-dimensional wheel is represented conceptually by an angle and distance from the center:

```text
x = extremity * cos(angle)
y = extremity * sin(angle)
```

The coordinate has independent values:

- **Direction or angle** selects the semantic region.
- **Extremity** measures distance from a neutral or balanced center.
- **Salience** measures how important the wheel is to the card.

Salience is the neutral internal term. Player-facing language may vary by wheel:

| Wheel | Possible presentation term |
| --- | --- |
| Elemental | Resonance |
| Ethos | Fervor |
| World Relation | Conviction |
| Cosmic Provenance | Devotion |
| Magical Tradition | Attunement |
| Manifestation | Manifestation |

Extremity and Salience must remain separate. Their combinations have different meanings:

| Extremity | Salience | Interpretation |
| --- | --- | --- |
| Low | Low | The wheel is irrelevant or the card is indifferent. |
| High | Low | The card has an incidental affinity that does not define its identity. |
| High | High | The card strongly embodies an extreme. |
| Low | High | Balance, synthesis, internal conflict, alternation, or paradox. |

## Center relationships and multiple poles

A centered coordinate alone cannot distinguish indifference from committed balance or simultaneous opposites. When Salience is high and Extremity is low, the generator may assign a relationship mode:

- **Equilibrium:** actively maintains balance;
- **Synthesis:** combines opposed principles into a coherent whole;
- **Conflict:** opposed principles struggle internally;
- **Alternation:** changes between poles;
- **Suppression:** one aspect contains or imprisons another;
- **Paradox:** embodies a normally impossible combination.

Complex cards may receive a secondary pole on the same wheel. The relationship mode explains how the poles interact. Additional poles and special relationships consume procedural complexity budget.

## Applicability and visible influence

Not every wheel should influence every card. Card family and context provide relevance weights. Lands may emphasize Elemental Affinity and Manifestation, while Actions may emphasize Ethos and Magical Tradition.

A conceptual influence calculation is:

```text
Influence = Salience * CardTypeRelevance * ContextRelevance
```

Complexity determines how many dominant influences become visible:

- simple cards normally express one dominant wheel;
- moderate cards express two;
- complex cards express three or four;
- exceptional cards may express multiple poles or explicit tensions.

Low-ranked coordinates may still guide minor statistics or visual details without appearing in the card's name or primary ability.

## Procedural naming

Naming consumes the same semantic profile as mechanics and art. It must not roll an independent theme.

Name lexicon entries are semantic records rather than interchangeable strings. Each entry may identify:

- one or more Lore Map concepts;
- semantic intensity;
- culture and historical register;
- emotional tone;
- part of speech and morphology;
- compatible card families;
- rarity of use;
- phonetic character;
- naming-template roles.

Synonyms may occupy different positions or intensities. For example, Spark, Ember, Flame, Blaze, and Inferno are related but not equivalent.

Card families use different grammatical templates. A Land, creature, relic, Action, and Plane Seed should not merely draw words from the same template. Naming ranks wheels by Salience and contextual relevance, then uses only the strongest few:

```text
Primary influence   -> central noun or identity
Secondary influence -> descriptor
Tertiary influence  -> epithet, provenance, or title
```

A highly salient centered wheel may contribute balance or conflict vocabulary even though its Extremity is low. A low-salience extreme normally remains a secondary mechanical or visual detail.

## Determinism

Canonical coordinates should use fixed-size integers rather than platform-dependent floating-point values. A possible representation is:

```text
WheelCoordinate:
  wheelId
  angle: 0..65535
  extremity: 0..65535
  salience: 0..65535
  relationshipMode: optional
  secondaryPoles: optional
```

The final encoding, sampling distributions, and deterministic trigonometric implementation remain technical decisions. Generator and Lore Map versions are compatibility-critical.

## Open questions

- Exact sectors and adjacency of the Elemental wheel.
- Sampling distribution for Salience and Extremity.
- Card-family relevance matrices.
- Complexity costs for secondary poles and relationship modes.
- Lexicon schema, cultural naming grammars, and localization.
- Whether Covenant–Sovereignty should become a second Cosmic Provenance axis.
