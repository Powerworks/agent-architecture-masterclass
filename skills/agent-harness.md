# HOW MVP? — Context wiring contract

## Agent entry point

- **Read first:** `README.md` of this org, then the ADR + `.feature` files of
  the repo you're working in.
- **Constraints are enforced, not suggested.** Failing guardrail = build fails;
  do not override from agent or human. Override path is *editing the rule and
  re-reviewing the ADR*, never `//noarchtest` comments.

## Single source of intent

All architectural intent lives in:

| Intent | Lives in | Consumed by |
|---|---|---|
| Rules embedded in specs | `*.feature` + ADRs | agents, fitness functions |
| Structural rules | ArchUnit rules | CI + agent feedback loop |
| Team ownership | `teams-as-code/` | CODEOWNERS, agent routing |
| Data topology | `make-the-grade-data-integrity/` | migrations, integrity jobs |

If intent lives only in a prompt, it will not survive the next model upgrade.
