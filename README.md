# agent-coding

High-signal coding workflow for a primary implementation agent collaborating with a human architect.

Use this skill for non-trivial coding tasks that need clear planning, scoped execution, and strong verification.

## What It Covers

- **Authority model** — human is the architect, agent is the hands
- **Plan mode** — structured planning for non-trivial tasks, lite mode for small changes
- **Task tracking** — shared execution ledger via `tasks/todo.md`
- **Verification** — never mark done without proof; frontend tasks require E2E coverage for changed user flows; escalate after repeated failures
- **Subagent strategy** — one task per subagent, no architectural authority
- **Core behaviors** — assumption surfacing, confusion management, push-back, simplicity enforcement, scope discipline
- **Execution efficiency** — no redundant reads, no redundant commands, batch edits, skip filler, plan before acting
- **Leverage patterns** — declarative goals, test-first, naive-then-optimize
- **Output standards** — direct communication, structured change descriptions, failure modes to avoid

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
