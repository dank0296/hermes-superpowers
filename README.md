# ⚡ Hermes Superpowers

**Spec-first development methodology for Hermes Agent.**

Stop letting your agent jump straight to code. This forces it to think first — brainstorm a spec, write a plan, then dispatch subagents that follow TDD. Inspired by [obra/superpowers](https://github.com/obra/superpowers), adapted for Hermes.

## The Chain

```
brainstorming        →  Spec doc written, user approved
       ↓
writing-plans        →  Tasks file written, user approved
       ↓
subagent-driven-dev  →  Tasks dispatched via delegate_task
       ↓
requesting-code-review → between task batches
       ↓
finishing flow        →  Tests pass, merge/PR/cleanup
```

## Skills Included

| Skill | What it does |
|-------|-------------|
| **brainstorming** | Socratic design partner — asks questions one at a time, proposes 2-3 approaches, saves spec to `.hermes/plans/` |
| **hermes-superpowers** | Phase detector — auto-routes to the right skill based on what files exist |

## Dependencies

These Hermes built-in skills complete the chain:

- `writing-plans` — break spec into bite-sized tasks
- `subagent-driven-development` — dispatch parallel subagents with two-stage review
- `test-driven-development` — enforce RED-GREEN-REFACTOR
- `requesting-code-review` — pre-merge quality gate

All four ship with Hermes. No extra install needed.

## Install

```bash
# Clone into your skills directory
git clone https://github.com/dank0296/hermes-superpowers.git ~/.hermes/skills/hermes-superpowers

# Or add as a skill source
hermes skills tap add dank0296/hermes-superpowers
```

## Usage

In any project, start with:

```
/skill hermes-superpowers
```

Then describe what you want to build. The agent auto-detects your phase:

```
📋 Phase: New Idea
→ Loading brainstorming...

What are you building? Walk me through the problem.
```

## Example

```
User: Build a CLI tool that backs up my Hermes config to GitHub
Agent: [Phase: New Idea → brainstorming]
       One question at a time:
       → Scheduled or manual?
       → Full config or just skills?
       → Encrypt the token?
       → [Presents 2 approaches, recommends one]
       → [User approves spec]

Agent: [Phase: Spec Approved → writing-plans]
       → 6 tasks, 18 min estimated

Agent: [Phase: Ready to Build → subagent-driven-development]
       → Batch 1: Tasks 1-3 dispatched
       → Between batches: requesting-code-review
       → Batch 2: Tasks 4-6 dispatched
       → All tests pass

Agent: [Phase: Branch Finish]
       → Merge to main? [y/n]
```

## Why This Works

Most coding agents fail because they **jump to code without understanding the problem.** This forces a spec-first loop:

1. **Extract clarity** — one question at a time, no assumptions
2. **Validate design** — section by section, before any code exists
3. **Plan in detail** — bite-sized tasks with exact file paths
4. **Execute in parallel** — subagents with isolated context
5. **Review between batches** — catch drift early

The result: autonomous coding sessions that run for hours without deviating from the plan.

## YouTube

[![Hermes Superpowers — Spec-First Development](https://img.youtube.com/vi/VIDEO_ID/0.jpg)](https://youtube.com/@DankAI)

## Credits

Methodology adapted from [obra/superpowers](https://github.com/obra/superpowers) by Jesse Vincent / Prime Radiant. Hermes adaptation by [@dank0296](https://github.com/dank0296).

## License

MIT