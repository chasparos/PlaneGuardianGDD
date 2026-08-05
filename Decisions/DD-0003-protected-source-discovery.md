# DD-0003 — Protected Source-Based Discovery

- **Status:** Accepted
- **Date:** 2026-08-01
- **Affected documents:** [Card Origins and Protected Discovery](../Procedural/Card_Origins_and_Protected_Discovery.md), [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md)

## Context

Players locate fragments of reality by supplying leads such as locations,
formulas, divinations, or arbitrary text. A public source-to-fragment hash
would allow automated offline mining for optimal fragments.

## Decision

Canonical source text, source type, and Era context map to an Origin ID through
a protected server-side cryptographic function. The resulting Origin ID
deterministically reconstructs the latent fragment and its eventual card,
while an atomic supply ledger controls global copies and per-account limits.

## Rationale

- Make repeated and shared sources reliably find the same card within an Era.
- Prevent cheap offline enumeration.
- Preserve deterministic card reconstruction from the permanent identifier.
- Turn knowledge of productive sources into a shareable social resource.

## Consequences

- Source canonicalization is a versioned compatibility rule.
- Fragment discovery requires server authority and an online enumeration cost or
  cooldown.
- Fragment state, card definition, and issued-copy state remain separate.
- Exhausted sources may reveal discovery history but cannot issue excess copies.
