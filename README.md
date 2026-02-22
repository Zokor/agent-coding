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

## Install

```bash
npx skills add Zokor/agent-coding
```

Recommended global install across detected agents:

```bash
npx skills add Zokor/agent-coding -g --agent '*' -y
```

## Management Commands

```bash
# Discover skill metadata without installing
npx skills add Zokor/agent-coding --list

# List installed skills
npx skills list

# Remove skill globally from all agents
npx skills remove agent-coding -g --agent '*' -y

# Check and update installed skills
npx skills check && npx skills update
```

## Migration from `agentic-coding`

The canonical skill name is now `agent-coding`.

If you still have `agentic-coding` installed, remove it:

```bash
npx skills remove agentic-coding -g --agent '*' -y
```

Then install `agent-coding`:

```bash
npx skills add Zokor/agent-coding -g --agent '*' -y
```
