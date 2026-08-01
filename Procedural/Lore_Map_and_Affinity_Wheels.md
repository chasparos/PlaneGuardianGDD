# Lore Map and Affinity Wheels

- **Status:** Foundational design
- **Related decisions:** [DD-0002](../Decisions/DD-0002-semantic-lore-map.md), [DD-0006](../Decisions/DD-0006-elemental-affinity-wheel.md), [DD-0011](../Decisions/DD-0011-manifestation-wheel.md), [DD-0012](../Decisions/DD-0012-magical-tradition-wheel.md), [DD-0013](../Decisions/DD-0013-cosmic-provenance-and-cosmology.md)
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

The wheel contains eight foundational elements arranged in this circular order:

```text
Radiance -> Fire -> Air -> Aether
    ^                         |
    |                         v
Earth <- Water <- Ice <- Shadow
```

Elements across the center form four oppositions:

| Element | Opposite | Fundamental tension |
| --- | --- | --- |
| Radiance | Shadow | Revelation–concealment |
| Fire | Ice | Heat–stillness |
| Air | Water | Ascent–depth and diffusion–cohesion |
| Earth | Aether | Matter–spirit and embodiment–transcendence |

These oppositions describe tension rather than morality. Radiance is not inherently good, and Shadow is not inherently evil. Ethos and Cosmic Provenance determine purpose and moral interpretation.

Earth replaces the overly broad idea of Physical as an element. It represents substance, weight, structure, and embodiment. Aether replaces Spiritual as an element and represents incorporeality, magical medium, and transcendence. Aether is an affinity; Astral Essence remains the resource that sustains planar reality.

#### Compounds and derived manifestations

Foundational elements may combine with each other and with other semantic wheels. Derived manifestations are reproducible outcomes, not additional foundational sectors.

| Manifestation | Typical semantic ingredients |
| --- | --- |
| Lightning | Fire + Air |
| Magma | Fire + Earth |
| Steam | Fire + Water |
| Mist | Water + Air |
| Crystal | Earth + Radiance, often with Order |
| Void | Aether + Shadow, possibly Annihilation |
| Necrotic energy | Shadow + Death |
| Spirit flame | Fire + Aether |
| Corrosion | Water + Earth + Transformation |
| Holy fire | Fire + Radiance + Divine |
| Hellfire | Fire + Infernal |
| Dream | Aether with Shadow or Radiance, expressed Ethereally |

Opposed elements may still combine when the card receives an appropriate relationship mode. Mist, for example, can express a Water–Air Synthesis. Such combinations consume complexity budget when they create a meaningful dual identity.

Poison, disease, and decay are effect families rather than foundational elements:

- **Poison** is a harmful material or spiritual substance whose elemental origin may vary.
- **Disease** is a transmissible process shaped primarily by Life–Death, often with Primal and Material influence.
- **Decay** is a process associated with Death and Transformation or Annihilation, sometimes reinforced by Shadow.

#### Affinity and effect delivery

Elemental affinity must remain separate from how an effect reaches and changes a target. An effect may independently define:

1. **Affinity:** Fire, Ice, Aether, or another elemental combination.
2. **Delivery:** physical, elemental, spiritual, or mental.
3. **Form:** slashing, piercing, impact, beam, wave, aura, or another geometry.
4. **Condition:** burning, frozen, shocked, poisoned, diseased, decaying, or another persistent state.

For example, Lightning Spear may use Fire–Air affinity, Elemental delivery, Piercing and Chained forms, and the Shocked condition. Spectral Talons may use Aether–Shadow affinity, Spiritual delivery, Slashing form, and a Soul Bleed condition.

### 2. Ethos

Uses two axes:

```text
Order <-> Chaos
Life  <-> Death
```

Life is not inherently good, and Death is not inherently evil. Example regions include ordered cultivation, wild adaptation, funerary inevitability, and entropic decay.

Ethos uses one wheel-level Salience value. Complex cards may receive an optional Focus such as Order–Chaos, Life–Death, Holistic, Center, or Cycle. Focus narrows interpretation without multiplying the normal naming branches. High-Salience centered cards may become active Champions of Balance rather than merely indifferent.

See [Ethos Wheel and Naming Vocabulary](Ethos_Wheel_and_Naming_Vocabulary.md).

### 3. World Relation

Uses two axes:

```text
Preservation <-> Transformation
Creation     <-> Annihilation
```

This wheel describes how a card relates to existence and change. Its regions include restoration, invention, purification through sacrifice, and dissolution. Destruction may appear as a process within Transformation; Annihilation means erasure rather than ordinary damage.

Ethos describes the state a card values; World Relation describes how it changes reality to pursue that value. See [World Relation Wheel and Flavor](World_Relation_Wheel_and_Flavor.md).

### 4. Cosmic Provenance

Uses the axis:

```text
Divine <-> Infernal
```

This describes greater cosmological lineage or authority, not morality. Divine beings may be tyrannical, while Infernal beings may be honorable or protective. The exact center is Worldly or Unaligned provenance: mortal, natural, arcane, self-wrought, or otherwise independent of Heaven and Hell.

The axis opens into two Universe-seeded structures. The pantheon is a relational wheel or network of gods whose strong Lore Map profiles create alliances, rivalries, and oppositions. Hell is a hierarchy whose infernals inherit, specialize, contest, and usurp authority. Gods and infernals are generated as powerful inhabitants of the Lore Map; they do not redefine it. See [Cosmic Provenance and Cosmology](Cosmic_Provenance_and_Cosmology.md).

### 5. Magical Tradition

Uses two axes:

```text
Arcane     <-> Primal
Controlled <-> Instinctive
```

This describes how an effect is accomplished. Its regions distinguish calculated Artifice, structured Ritual, instinctive Sorcery, and untamed Wilding. The exact center is Mundane: work performed through labor, tools, training, logistics, patience, and time rather than supernatural technique. A highly salient center makes mundanity part of the card's identity; low Salience means that method is irrelevant.

Mundane effects tend to require fewer magical or exotic resources but take longer to complete or recover from. This is a balancing tendency, not a universal cost formula. See [Magical Tradition Wheel and Flavor](Magical_Tradition_Wheel_and_Flavor.md).

### 6. Manifestation

Uses two axes:

```text
Embodied    <-> Incorporeal
Rooted      <-> Wandering
```

This describes how and where a card exists. Embodied–Incorporeal measures dependence on a stable physical form; Rooted–Wandering measures dependence on a particular locus, host, source, or anchor. It distinguishes foundations, imprints, pilgrims, hauntings, caravans, migrating creatures, dreams, and astral currents.

Earth–Aether describes elemental resonance, not manifestation. Earth does not require embodiment, and Aether does not require incorporeality. See [Manifestation Wheel and Flavor](Manifestation_Wheel_and_Flavor.md).

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
  focus: optional
  secondaryPoles: optional
```

The final encoding, sampling distributions, and deterministic trigonometric implementation remain technical decisions. Generator and Lore Map versions are compatibility-critical.

## Open questions

- Exact angular width and boundary behavior of Elemental sectors.
- Thresholds and complexity costs for compound manifestations.
- Resistance rules for affinity, delivery, form, and condition layers.
- Sampling distribution for Salience and Extremity.
- Card-family relevance matrices.
- Complexity costs for secondary poles and relationship modes.
- Lexicon schema, cultural naming grammars, and localization.
- Exact pantheon sizing, opposition rules, and infernal rank vocabulary.
- How cosmological offices and hierarchies change between Eras.
