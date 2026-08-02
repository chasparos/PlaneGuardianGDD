# Client and Server Architecture

- **Status:** Foundational platform direction; detailed implementation remains open
- **Related decision:** [DD-0019](../Decisions/DD-0019-java-platform-and-first-plane-flow.md)
- **Related documents:** [PlaneGuardian GDD](../GDD/PlaneGuardian_GDD.md), [Time, Combat, and Cross-Plane Effects](../GDD/Time_Combat_and_Cross_Plane_Effects.md), [First Plane Onboarding](../GDD/First_Plane_Onboarding.md)

## Target platform

- **Client:** Java with jMonkeyEngine 3.
- **Server:** authoritative pure Java NIO TCP service.
- **Development persistence:** H2.
- **Production persistence:** undecided; PostgreSQL is the preferred current
  migration target.
- **Initial desktop runtime:** exact Java LTS version remains to be selected
  after jME3 and LWJGL compatibility testing.

A shared Java language permits deterministic generation, protocol models, and
selected validation code to be reused while maintaining strict client/server
authority boundaries.

## Client states

The client should use explicit application states for Boot and Splash,
Loading, Authentication, Game Menu, First-Plane Onboarding, Main Stage,
construction overlays, card inspection, and combat reports.

The Main Stage owns the 3D Plane scene. UI and procedural visuals remain
data-driven rather than hard-coded per card.

## Client rendering responsibilities

The client deterministically composes ordinary visual assets from card
identity, presentation metadata, and a pinned art-generator version. Likely
systems include:

- procedural island assembly;
- biome and affinity materials;
- modular landmarks and creature silhouettes;
- bridge and Stability states;
- Void shader and parallax layers;
- render-to-texture card portraits;
- LOD, culling, instancing, and texture atlases;
- disk cache keyed by identity and visual version.

The server sends authoritative identity, rules, mutable state, and approved
presentation overrides rather than transmitting generated ordinary artwork.

## Server execution shape

```text
NIO selector threads
  -> framed protocol decoding
  -> authentication and validation
  -> command dispatch
  -> per-Plane serialized execution
  -> simulation and domain services
  -> persistence workers
```

Selector threads must not block on database access or expensive simulation.
Plane mutations are serialized so lazy advancement, Operations, combat
consequences, and externally submitted transactions observe one authoritative
order.

## Protocol direction

The TCP protocol should provide:

- explicit length-prefixed framing;
- protocol and schema version;
- message type;
- request and correlation identifiers;
- authentication and authorization context;
- sequence or revision information;
- bounded payload sizes;
- deterministic validation errors;
- idempotency where retries are possible;
- encrypted transport.

Java native object serialization is not used as the wire format. The eventual
binary codec remains open. Correct use of Java `SSLEngine` is substantial;
terminating TLS through a suitable front proxy is also a valid deployment
option if end-to-end authority and connection identity remain sound.

## Simulation and numeric state

The server stores authoritative timestamps, generator versions, and mutable
state. Economy and generation calculations should use integer or fixed-point
values where reproducibility matters. Floating-point presentation calculations
must not become authoritative state accidentally.

Lazy Plane simulation runs when a Plane is touched or when an external command
must change it. The same deterministic event ordering handles ordinary offline
advancement and explicit Plane-time advancement.

## Persistence boundary

H2 is a development convenience rather than a promise that production SQL will
behave identically. Persistence uses:

- JDBC-facing repository interfaces;
- explicit transactions;
- versioned migrations through a tool such as Flyway or Liquibase;
- portable SQL where practical;
- no dependence on H2-specific locking or identity behavior;
- production-style PostgreSQL integration tests early in development;
- backup and restore testing before persistent public play.

Running PostgreSQL on the same small VM may be the simplest early-alpha
deployment. A managed database becomes attractive when backups, availability,
and player-owned value justify the operational cost.

## Current low-cost hosting notes

Provider offers are volatile. This section records options reviewed on
2026-08-02 and is not a foundational commitment.

- [Oracle Cloud Free Tier](https://www.oracle.com/cloud/free/) currently
  advertises Always Free AMD and Ampere A1 compute. A normal VM is a strong
  functional fit for an always-on raw TCP Java server, subject to regional
  capacity and account availability.
- [Google Compute Engine](https://cloud.google.com/products/compute) currently
  advertises one free `e2-micro` VM, 30 GB standard persistent disk, and 1 GB
  monthly outbound transfer. Memory and egress are restrictive for a JVM plus
  database but may suit a private test server.
- [Hetzner cost-optimized cloud](https://www.hetzner.com/cloud/cost-optimized)
  currently lists inexpensive shared VMs and is a practical low-friction paid
  option, especially for a European alpha.
- [Neon plans](https://neon.com/docs/introduction/plans) and [Supabase billing](https://supabase.com/docs/guides/platform/billing-on-supabase)
  currently include free PostgreSQL-oriented plans. Scale-to-zero, pausing,
  remote latency, quotas, and connection behavior require testing before use by
  an always-connected game server.

HTTP-oriented free web-service platforms are often a poor fit for a publicly
reachable arbitrary TCP protocol. A small VM should be the default deployment
assumption until a provider is verified to expose persistent raw TCP.

## Provisional deployment progression

1. Local H2 for rapid development.
2. Automated PostgreSQL compatibility and migration tests.
3. Free VM for private network testing where available.
4. Small paid VM with colocated PostgreSQL for early persistent alpha.
5. Managed PostgreSQL and separated services when reliability requires them.

## Open questions

- Java runtime, jME3, LWJGL, UI toolkit, and packaging versions.
- Wire codec, compression, TLS termination, and reconnect protocol.
- Selector count, worker pools, per-Plane scheduling, and backpressure.
- Authentication, credential recovery, account verification, and abuse control.
- Exact persistence schema, migration tool, and PostgreSQL compatibility policy.
- Deployment region, provider, backups, observability, and disaster recovery.
- Asset-cache limits, invalidation, approved-art delivery, and patching.
