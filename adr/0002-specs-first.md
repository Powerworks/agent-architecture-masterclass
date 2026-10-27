# ADR 0002 — Specs are executable first; code second

Status: **Accepted**

## Context

The workshop's core move is: **architecture rules embedded in
specifications**, the *same* rules generating deterministic guardrails.
Agentic codegen fails silently without a spec to interpolate from.

## Decision

Every exercise repo contains a Gherkin (`.feature`) spec stating the invariant
*before* the implementation that enforces it. Generating concrete fitness
functions from specs is exercise #1's whole point; we dog-food it from the top.

## Consequences

- ADRs and features are reviewed in PRs before the code that enforces them.
- Fitness functions are traceable: `Feature → Rule → Test` (each ArchUnit rule
  cites its feature line).
- An LLM interpolating into code has a *single source of intent* to interpolate
  from — the spec, not tribal memory.
