# Agentic Architecture Masterclass — Working Replica

A hands-on, working replica of Neal Ford's masterclass
**"How to Teach Your Agents About Architecture"** — nine intersections of software
architecture with human-and-agentic code generation, rebuilt repo by repo with
durable, fundamentals-first tooling (nothing here depends on a LLM to stay
valuable in five years).

> **Core thesis of the class:** *Ephemerality decides how much architecture you
> need.* Vibe-coded throwaways need none. **Non-ephemeral code — the foundation
> future building stands on — needs deterministic guardrails, because even the
> best models must be trusted *but verified*.**

## The nine intersections & where each is implemented

| Intersection | Repo | Exercise it covers |
|---|---|---|
| **GenAI / wiring** | this repo | WHY? — prompt → context → harness engineering |
| **Implementation** | [`make-the-grade`](https://github.com/Powerworks/make-the-grade) | The case-study system under test (kata, language-agnostic spec) |
| **Implementation guardrails** | [`make-the-grade-guardrails`](https://github.com/Powerworks/make-the-grade-guardrails) | Exercise: Make the Grade guardrails |
| **Architecture Definition Language** | [`agent-architecture-adl`](https://github.com/Powerworks/agent-architecture-adl) | Exercise: generating concrete fitness functions (LLM as interpolator) |
| **Engineering (VCS churn)** | [`copy-paste-policy`](https://github.com/Powerworks/copy-paste-policy) | Exercise: how much copy/paste is OK? |
| **Integration (coupling)** | [`coupling-fitness-functions`](https://github.com/Powerworks/coupling-fitness-functions) | Exercises: limiting static & dynamic coupling |
| **Infrastructure (CALM → ADL)** | [`calm-to-adl`](https://github.com/Powerworks/calm-to-adl) | Exercise: translate CALM to ADL |
| **Data** | [`make-the-grade-data-integrity`](https://github.com/Powerworks/make-the-grade-data-integrity) | Exercise: Make the Grade data integrity |
| **Team topologies** | [`teams-as-code`](https://github.com/Powerworks/teams-as-code) | WHO? — representing teams in Architecture as Code |

## Why these repos exist

Every exercise artifacts something **deterministic**: architecture rules written
*as code* (ADRs, ADL, ArchUnit, Gherkin, YAML, SQL), wired into the places where
agents work — specs, CI, and agent harness. The class's arc maps to this repo
structure exactly:

```
WHY?   → skills/agent-harness.md, kata/ (spec-first)
HOW?   → agent-architecture-adl (ADL → fitness functions)
WHAT?  → make-the-grade-guardrails (structure/constraint/governance)
WHERE? → copy-paste-policy, coupling-fitness-functions, calm-to-adl,
         make-the-grade-data-integrity
WHO?   → teams-as-code
WHEN?  → adl/ + guardrails are the mesh: same rules, agent context + CI gates
```

## How to re-run the class on yourself

1. `make-the-grade` — read the kata spec, mark which parts you'd agent-generate
   vs. write yourself. Build: `mvn verify`.
2. Guardrails *before* changing code: add a failing ArchUnit rule to
   `make-the-grade-guardrails`, watch CI catch it.
3. ADL repo: write one ADL rule, run the interpolator, read the generated
   fitness function.
4. Copy-paste: run the duplication scorer, decide a threshold *in policy*,
   not in the tool default.
5. Coupling: generate the dependency matrix; compare against the quantum
   boundaries you *thought* you had.
6. Data integrity: review the split plan *before* needing it; read the
   consistency saga contract.
7. Teams: edit `teams-as-code/teams.yaml`, regenerate CODEOWNERS, notice how the
   architecture documentation correctly falls out.

## Reproduction notes (honesty section)

- No upstream course repos exist — Neal Ford runs this class entirely live. This
  replica was reconstructed from the public outline + known kata sources, using
  explicit assumptions (each repo states its own).
- Everything is asserted, not asserted-at: Java is compiled and tests run,
  Python generators are pytest-verified, SQL is linted for structural integrity.
- A real class would add exercise solutions *during* the workshop; empty gaps are
  intentional invitation space.

## License

CC BY-SA 4.0 — share the pattern, keep the attribution.
