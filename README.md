# agent-coding

Structured workflow formats for planning, tracking, assumptions, and change documentation in multi-step coding tasks.

## What It Covers

- **Plan mode** — structured planning for non-trivial tasks (PLAN / PLAN LITE formats), lite mode for small changes
- **Task tracking** — shared execution ledger via `tasks/todo.md`
- **Verification** — never mark done without proof; frontend tasks require E2E coverage for changed user flows
- **Self-improvement** — capture correction patterns in `tasks/lessons.md`
- **Assumption surfacing** — explicit ASSUMPTIONS I'M MAKING format before non-trivial work
- **Execution efficiency** — no redundant reads, no redundant commands, batch edits, skip filler, plan before acting
- **Leverage patterns** — declarative goals, test-first, naive-then-optimize
- **Change descriptions** — structured CHANGES MADE / THINGS I DIDN'T TOUCH / POTENTIAL CONCERNS output

## Benchmark

Tested against 3 evals (multi-step refactor, bug fix with ambiguity, feature addition) with 15 total assertions covering planning discipline, assumption surfacing, security awareness, scope discipline, and code correctness.

| Configuration | Pass Rate | Avg Tokens | Avg Time |
|---------------|-----------|------------|----------|
| **With skill** | **100%** (15/15) | 15,496 | 53.6s |
| Without skill | 80% (12/15) | 10,617 | 39.2s |
| **Delta** | **+20pp** | +4,879 | +14.4s |

Key differentiators vs baseline:
- **Planning**: Skill always produces explicit PLAN and ASSUMPTIONS blocks; baseline skips them
- **Security awareness**: Skill identifies all issues including hardcoded secrets (flags out-of-scope ones without fixing); baseline misses some
- **Scope discipline**: Skill uses structured CHANGES MADE / THINGS I DIDN'T TOUCH / POTENTIAL CONCERNS output
- **Verification**: Skill adds verification steps (e.g., route-by-route equivalence audit on refactors)

## Installation

Install with `npx skills add` only.

```bash
# Project-local (writes under current repo)
npx -y skills add Zokor/agent-coding --skill agent-coding --agent claude-code codex --yes

# Global (writes under home directory)
npx -y skills add Zokor/agent-coding -g --skill agent-coding --agent claude-code codex --yes
```

- Project-local install creates `./.agents/skills/agent-coding` and links `./.claude/skills/agent-coding`.
- Global install creates `~/.agents/skills/agent-coding` and links `~/.claude/skills/agent-coding`.

Useful management commands:

```bash
# List skills exposed by the repo
npx -y skills add Zokor/agent-coding --list

# List installed skills
npx -y skills list

# List globally installed skills
npx -y skills list -g

# Check and apply skill updates
npx -y skills check && npx -y skills update
```

## Migration from `agentic-coding`

The canonical skill name is now `agent-coding`.

If you still have `agentic-coding` installed, remove it:

```bash
npx -y skills remove agentic-coding -g --agent '*' --yes
```

Then install `agent-coding`:

```bash
npx -y skills add Zokor/agent-coding -g --skill agent-coding --agent claude-code codex --yes
```
