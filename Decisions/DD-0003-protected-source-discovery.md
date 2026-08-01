# DD-0003 — Protected Source-Based Discovery

- **Status:** Accepted
- **Date:** 2026-08-01
- **Affected documents:** [Card Origins and Protected Discovery](../Procedural/Card_Origins_and_Protected_Discovery.md), [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md)

## Context

Players discover cards by supplying sources such as summoning phrases, locations, formulas, or arbitrary text. A public source-to-card hash would allow automated offline mining for optimal cards.

## Decision

Canonical source text, source type, and Era context map to an Origin ID through a protected server-side cryptographic function. The resulting Origin ID deterministically reconstructs the card, while an atomic supply ledger controls global copies and per-account limits.

## Rationale

- Make repeated and shared sources reliably find the same card within an Era.
- Prevent cheap offline enumeration.
- Preserve deterministic card reconstruction from the permanent identifier.
- Turn knowledge of productive sources into a shareable social resource.

## Consequences

- Source canonicalization is a versioned compatibility rule.
- Discovery requires server authority and an online enumeration cost or cooldown.
- Card definition and issued-copy state remain separate.
- Exhausted sources may reveal discovery history but cannot issue excess copies.
