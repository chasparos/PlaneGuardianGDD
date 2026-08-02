# Card Zones and Attachments

- **Status:** Foundational design with provisional terminology and rates
- **Related decisions:** [DD-0015](../Decisions/DD-0015-card-zones-attachments-and-commitment.md), [DD-0020](../Decisions/DD-0020-3d-land-and-attachment-visual-contract.md)
- **Related documents:** [PlaneGuardian GDD](PlaneGuardian_GDD.md), [Plane Economy and Operations](../Economy/Plane_Economy_and_Operations.md), [Combat and Raiding](Combat_and_Raiding.md), [Land and Attachment Visual Contract](../Art/Production_Guides/Land_and_Attachment_Visual_Contract.md)

## Purpose

Card zones define where an owned card instance can be committed and which
rules govern it there. The model must keep Plane construction readable while
allowing unusual combinations through explicit card text.

## Plane-building interface

The intended builder can present:

- the collection on the right;
- the ordered Land list on the left;
- the selected Planar Seed as the list header;
- attachment slots beside each selected Land;
- a small hex-ring adjacency preview;
- detailed neighbor effects on hover or selection.

Exact UI layout remains implementation work, but the rules should preserve this
clear one-dimensional editing surface over the generated hex geometry.

## Deployment structures

Three concepts remain distinct:

| Concept | Meaning |
| --- | --- |
| Local slot | One card may attach to a particular host instance |
| Plane-wide budget | Lands and other cards determine total configured capacity |
| Eligibility | Broad condition that permits a card or role to be deployed |

A Mountain may make Rocs eligible. The defensive budget determines whether a
particular Roc fits. An attachment slot is not involved unless another rule
explicitly attaches the Roc to a host.

## Working card taxonomy

Top-level families should describe deployment grammar rather than every
fictional distinction. Current working families are:

- Plane Seed;
- Land;
- Enhancement;
- Entity;
- Action;
- Operation-only card;
- Event;
- Relic.

Creature, Hero, and Squad are Entity subtypes. Structure, Facility,
Enchantment, Location, Settlement, Fortification, Shrine, and Lair are normally
Enhancement subtypes or tags. Equipment, Implement, Treasure, and Banner may be
Relic subtypes.

These names remain provisional. The important distinction is between
deployment grammar, broad subtype, and searchable mechanical tags.

## Land hexes and Enhancement slots

Only Lands create ordinary hex tiles. Enhancements develop a host Land rather
than consuming another terrain position.

Provisional slot distribution is:

- no Enhancement slot: 79.9% of Lands;
- one Enhancement slot: 20% of Lands;
- two Enhancement slots: 0.1% of Lands.

Slot generation consumes Power and Complexity budget and normally raises the
Land's base Astral Essence upkeep even while empty. Attached cards add their
own upkeep. A slotless Land can spend its budget on stronger intrinsic output,
adjacency, storage, capacities, eligibility, or abilities.

The slot is therefore an economic commitment rather than a universal upgrade.

## Compatibility philosophy

### Hard legality

Hard constraints establish coherent objects and should be rare and broad:

- Land Enhancements require a compatible Land-host slot;
- Equipment requires a compatible Entity or other printed host;
- Operation-only cards enter the recurring Plane pile;
- Battle Events occupy eligible tactical or timed zones;
- one card instance cannot occupy two zones.

Strong thematic eligibility such as a Roc requiring a Mountain is permitted
sparingly. Such requirements should use broad attainable tags, and multiple
cards or effects may provide those tags.

### Soft compatibility

Most semantic mismatch should remain playable and appear as:

- increased or reduced upkeep;
- local Stability;
- cooldown changes;
- weakened or strengthened output;
- dormant abilities;
- adjacency bonuses and penalties.

An Incorporeal Enhancement should not normally require rare permission merely
to attach. A host may instead remove its penalty, reduce its upkeep, or grant a
synergy.

### Printed synergy

Printed rules reward desirable combinations without making everything else
illegal. Examples include benefits for Facilities, Primal Enhancements,
Fortifications, Incorporeal attachments, or specific semantic tags.

The guiding rule is:

> Hard constraints establish coherent deployment. Soft modifiers and bonuses
> establish strategy.

## Visual attachment contract

Legal attachments retain their card identity on every host. The attached card
owns its primary 3D model, silhouette, dominant palette, materials, and native
effects. The Land owns only the contact seam through bounded tint, decals,
overlays, reflected light, and interaction effects.

Semantic mismatch therefore remains visible. A Verdant Oak played on a Death
Land stays alive and green; ash or pale lichen may gather at its roots without
turning the entire attachment into an undead tree. The presentation reinforces
the soft-compatibility rules instead of implying an unprinted hard restriction.

The system should use reusable 3D models and host-blend masks rather than
generating a bespoke model for every legal combination. See the production
guide for the detail budget and validation contract.

## Lands as Plane-wide enablers

Lands may influence:

- recurring Operations pile capacity or behavior;
- Rift defense deployment budget;
- Battle Event capacity;
- troop eligibility;
- formation and reserve capacity;
- Action Deck capacity;
- Safe Storage;
- future automation and delegation rules.

A slotless Mountain may be valuable because it enables Rocs and Air Battle
Events. A Barony-tagged Land may expose a Hero or Leader attachment slot.

## Card definition, copy, and commitment

A deterministic card definition describes shared generated mechanics and
presentation. Each owned copy is a card instance with its own assignment,
cooldown, and mutable history.

One instance may occupy only one committed role. A Hero cannot simultaneously
serve as General, Expedition Commander, Baron, and Instructor. If the player
owns several permitted copies, each may be deployed independently.

Unique cards have only one global instance. Lower-scarcity definitions may
support extremely large supply, subject to Universe supply and account rules.

## Broadly typed host slots

Unusual attachments require an explicit host contract rather than arbitrary
pairing. Possible host slot concepts include:

- Land Enhancement;
- Equipment;
- Retainer;
- Domain;
- Baron;
- Instructor;
- Familiar;
- Oath;
- Command Support.

A General may expose a Domain slot that accepts a Land instance. That Land is
not terrain and contributes only its printed Domain interpretation. A Training
Facility may expose an Instructor slot for a Hero with Leader. These examples
demonstrate the architecture rather than settling exact cards.

## Nested attachments

The attachment model may form a rooted acyclic tree. Every additional edge
adds upkeep and consumes rules Complexity. Depth-two combinations can support
special builds; deeper combinations should require exceptional printed
permission or may be disallowed in the initial implementation.

The UI should show nested cards through expandable detail or breadcrumbs
rather than placing an unlimited tree beside the Land list.

## Future automated Actions

Some future host may delegate an eligible Action to resolve without player
interaction, such as a recurring quest or resource expedition. This remains
future work. Ordinary Actions stay in player space and are not automatically
eligible for the Plane's recurring pile.

## Open questions

- Final family names and the in-world name of the recurring Operations pile.
- Exact slot Power cost, upkeep burden, and nested-depth surcharge.
- Attachment removal, host dormancy, cooldown, and replacement lifecycle.
- Default maximum attachment depth.
- Which broad eligibility requirements deserve hard legality.
- Exact Plane-wide budgets contributed by Lands and Seeds.
- Collection filtering and UI presentation for legal and synergistic cards.
