# ADR 0001 — Replication language & stack: Java 21, plain JUnit, no framework

Status: **Accepted** (reconstructed masterclass)

## Context

The class needs a case-study system ("Make the Grade") that:

- is the substrate for **implementation guardrails** (layering, dependencies),
- compiles **deterministically** without network-dependent framework magic,
- demonstrates packaging/quantum boundaries without framework indirection.

## Decision

Plain Java 21 (records, text blocks, `List.of`) + JUnit 5, built with Maven.
No Spring. Modules enforce source-level boundaries so ArchUnit rules test the
*actual* structure, not an auto-wired one.

## Consequences

- Fast, hermetic `mvn verify` (no container/startup tax).
- Layering is visible in `javap`/imports — perfect for coupling matrices.
- Students/agents see the architecture, not a framework's convention engine.
