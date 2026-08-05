# DD-0019 — Java Platform and First Plane Flow

- **Status:** Accepted
- **Date:** 2026-08-02
- **Affected documents:** [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md), [First Plane Onboarding](../GDD/First_Plane_Onboarding.md), [Client and Server Architecture](../Technical/Client_Server_Architecture.md)

## Context

The game needs a concrete target platform and a first-run flow that introduces
its identity through play. Starter generation must guarantee useful card
families without weakening deterministic generation or manipulating completed
hash bytes in ad hoc ways.

## Decision

The target client is Java with jMonkeyEngine 3. The authoritative game server
is a pure Java NIO TCP service. H2 is the development persistence layer behind
repository interfaces and versioned migrations; the final production database
and hosting provider remain deployment decisions, with PostgreSQL the current
preferred migration target.

The application flow is:

```text
Splash -> Loading -> Login or Account Creation -> Game Menu -> Main Stage
```

A new account enters first-Plane onboarding within the Main Stage. The player
receives the “Awaken, Guardian” setting introduction, is entrusted with an
unsprouted Planar Seed, answers a small semantic questionnaire, locates and
activates a coherent common starter collection, and uses a special Action to
realise a slightly higher-Quality Hero guaranteed to have Leader.

Starter families are selected by an authoritative versioned generation
context. Independent domain-separated random streams derive family,
semantics, mechanics, name, and art. Completed hashes are not modified with
XOR or similar post-processing to force card type.

## Rationale

One Java stack simplifies shared deterministic code and deployment. NIO suits
an authoritative touch-driven simulation, while H2 keeps development light.
Onboarding in the empty Main Stage lets the central fantasy unfold visibly.
Domain separation guarantees necessary starter roles without creating
correlated hashes or weakening protected discovery.

## Consequences

- Selector threads must never block on simulation or database access.
- The network protocol requires explicit framing, versioning, request identity,
  validation, authentication, and transport encryption.
- Production-style PostgreSQL integration tests should begin before final
  hosting even while H2 remains the local default.
- The starter Leader must harmonize with the Seed and questionnaire without
  becoming a perfect universal answer.
- Starter trading, binding, reroll protection, exact questionnaire, Java
  runtime version, production database, and hosting remain open.
