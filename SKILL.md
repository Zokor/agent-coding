---
name: agent-coding
description: Structured workflow formats for planning, tracking, assumptions, and change documentation in multi-step coding tasks.
---

# Agent Coding Skill

Workflow formats and patterns for multi-step coding tasks. Provides structured planning, task tracking, assumption surfacing, and change documentation to keep agent-human collaboration high-signal and reviewable.

## Workflow Orchestration

### Plan Mode (Critical)
Enter Plan Mode for any task that involves:
- 3+ meaningful steps
- Architectural or data-model decisions
- Non-trivial refactors
- User-visible or cross-system behavior changes

Format:

```text
ASSUMPTIONS:
1. [assumption about runtime, environment, or requirements]
2. [assumption about existing patterns or constraints]

PLAN:
1. [step] - [why]
2. [step] - [why]
3. [step] - [why]
-> Executing unless you redirect.
```

Every plan starts with assumptions — surface what you're inferring so the human can correct before you write code.

Rules:
- Specifications come before code.
- Verification steps are part of the plan.
- If reality diverges from the plan: STOP and re-plan.

### Plan Mode (Lite)
Use Plan Mode (Lite) only when the change is:
- Localized
- Non-architectural
- Clearly reversible

Format:

```text
ASSUMPTIONS: [brief, inline — e.g. "existing patterns authoritative, no breaking changes needed"]

PLAN (LITE):
- What I'm changing
- Why it's safe
- How I'll verify
-> Proceeding unless you object.
```

### Task Tracking (High)
1. Write the plan to `tasks/todo.md` as checkable items (create if missing).
2. Check in before starting implementation.
3. Mark items complete as you go.
4. Add a `Review` section when finished.

This file is the shared execution ledger and source of truth.

### Verification Before Done (Critical)
Never mark a task complete without proof.

You must:
- Run tests or equivalent verification.
- Check logs or outputs when relevant.
- Diff old vs new behavior when behavior changes.
- **Frontend tasks**: e2e tests covering the changed user flow are required as part of done. Follow conventions in [`agent-conventions/frameworks/frontend/e2e.md`](../agent-conventions/frameworks/frontend/e2e.md) (or search for `e2e.md` under the `agent-conventions` skill if the relative path differs).

### Self-Improvement Loop (High)
After a correction from the human:
1. Update `tasks/lessons.md` (create if missing).
2. Capture the general pattern, not a one-off detail.
3. Write a rule that would have prevented the mistake.

Lessons hygiene:
- Merge similar lessons.
- Prefer durable rules over situational fixes.

## Execution Efficiency (High)
Minimize wasted cycles. Every tool call, re-read, and summary costs time and attention.

- **Never re-read files you just wrote or edited.** You know the contents.
- **Never re-run commands to "verify" unless the outcome was uncertain.** Deterministic operations don't need confirmation runs.
- **Don't echo back large blocks of code or file contents unless asked.** The human can see the file.
- **Batch related edits into single operations.** Don't make 5 edits when 1 handles it.
- **Skip filler phrases.** No "I'll continue...", "Let me now...", "Great, moving on..." — just do it.
- **Plan before acting.** If a task needs 1 tool call, don't use 3.
- **Keep updates concise, but summarize actions and outcomes at meaningful checkpoints.** Include raw command output when requested or when verification depends on it.

## Leverage Patterns

### Declarative Over Imperative
Reframe step-by-step instructions as goals:

```text
I understand the goal is [success state]. I'll work toward that and show you when it's achieved.
```

### Test-First Leverage
For non-trivial logic:
1. Write the test that defines success.
2. Implement until it passes.
3. Show both.

### Naive Then Optimize
1. Implement the obviously correct version.
2. Verify correctness.
3. Optimize without changing behavior.

Correctness precedes performance.

## Change Description
For multi-file or 10+ line changes:

```text
CHANGES MADE:
- [file]: [what and why]

THINGS I DIDN'T TOUCH:
- [file]: [intentionally left alone]

POTENTIAL CONCERNS:
- [risks or verification points]
```

Skip for trivial changes.
