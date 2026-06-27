---
name: hermes-superpowers
description: "Orchestration meta-skill. Load at session start in any project. Detects current development phase and routes to the right sub-skill. Chains brainstorming → writing-plans → subagent-driven-development → review → finish."
version: 1.0.0
author: agent
license: MIT
metadata:
  hermes:
    tags: [orchestration, methodology, workflow, superpowers]
    related_skills: [brainstorming, writing-plans, subagent-driven-development, test-driven-development, requesting-code-review, plan]
---

# Hermes Superpowers — Spec-First Development

A cohesive software development methodology. Detects your current phase and chains the right skills together. Inspired by obra/superpowers, adapted for Hermes.

## SUBAGENT SKIP

If you were dispatched as a subagent to execute a specific task, skip this skill entirely. It's for the parent session only.

## Hard Rules

1. **Check for relevant skills before ANY action.** Even a 1% chance a skill applies = load it. The skills exist to prevent undisciplined code-from-hip.
2. **User instructions override skills.** If the user says "skip the spec, just code it" — you obey. But if they haven't opted out, the workflow runs.
3. **Phase detection happens first.** Before writing code, answering questions, or even exploring the codebase — detect what phase you're in.

## Phase Detection

Check `.hermes/plans/` for these files. The most recent file determines your phase:

| Files Found | Phase | Action |
|---|---|---|
| Nothing | **New idea** | Load `brainstorming` skill |
| `<date>-<topic>-spec.md` exists, no tasks file | **Spec approved** | Load `writing-plans` skill |
| `<date>-<topic>-tasks.md` exists, incomplete | **Ready to build** | Load `subagent-driven-development` |
| `<date>-<topic>-tasks.md` exists, all done | **Branch finish** | Present merge/PR/cleanup options |
| None of the above, but user says "fix bug" | **Debug** | Load `systematic-debugging` skill |

## Skill Chain

```
brainstorming        →  Spec doc written, user approved
       ↓
writing-plans        →  Tasks file written, user approved
       ↓
subagent-driven-dev  →  Tasks dispatched via delegate_task
       ↓                    ↓
requesting-code-review ← between task batches
       ↓
finishing flow        →  Tests pass, merge/PR/cleanup
```

## The Workflow

### Phase: New Idea
You're starting fresh. No spec exists.

1. Load `brainstorming` skill via `/skill brainstorming`
2. Follow it exactly — ask questions, propose approaches, present design
3. Save spec to `.hermes/plans/YYYY-MM-DD-<topic>-spec.md`
4. Gate: do not proceed until user approves the spec

### Phase: Spec Approved
A spec exists. Time to plan the build.

1. Load `writing-plans` skill via `/skill writing-plans`
2. Read the spec file first — work from the approved design
3. Break into bite-sized tasks (2-5 min each)
4. Save to `.hermes/plans/YYYY-MM-DD-<topic>-tasks.md`
5. Gate: do not proceed until user approves the plan

### Phase: Ready to Build
Tasks file exists with incomplete items.

1. Load `subagent-driven-development` skill
2. Use `delegate_task` for each task or batch
3. Between batches, load `requesting-code-review`
4. Subagents must use `test-driven-development` skill
5. Track progress: mark tasks complete in the tasks file

### Phase: Bug Fix
User reports a bug, not a new feature.

1. Load `systematic-debugging` skill
2. Root cause first — no band-aids
3. After fix: write a test that proves it was broken
4. Small bugs: skip the full spec/plan chain
5. Large bugs that need redesign: treat as "new idea" and brainstorm

### Phase: Branch Finish
All tasks complete. Time to land the work.

Present options based on the repo:
- **GitHub repo**: Open a PR, run CI
- **Personal project**: Merge to main, clean up worktree
- **Prototype/spike**: Keep on branch, document findings
- **Discard**: If this was an experiment that didn't work out

Checklist:
1. All tests pass
2. No lint errors
3. Spec doc is committed
4. Tasks file shows all complete
5. Ask: "Merge to main, open a PR, keep on branch, or discard?"

## Red Flags — Stop and Check

| You think... | Reality |
|---|---|
| "This is just a simple question" | Questions are tasks. Check phase. |
| "I'll explore the codebase first" | Skills tell you HOW to explore. Check first. |
| "This is too simple for a spec" | Simple things hide assumptions. Even two sentences count. |
| "I remember how that skill works" | Skills evolve. Load the current version. |
| "Let me just do this one thing first" | Undisciplined action wastes time. Phase check prevents this. |

## Response Template

After phase detection, start with a one-line status:

```
📋 Phase: [New Idea / Spec Approved / Ready to Build / Bug Fix / Branch Finish]
→ Loading [skill name]...
```

This keeps you and the user aligned on where you are in the workflow.

## File Conventions

| File | Location |
|---|---|
| Spec (design doc) | `.hermes/plans/YYYY-MM-DD-<topic>-spec.md` |
| Tasks (implementation plan) | `.hermes/plans/YYYY-MM-DD-<topic>-tasks.md` |
| Project context | `AGENTS.md` or `CLAUDE.md` in repo root |

## Pitfalls

- **Skipping phase detection** — the most common failure mode. Always check `.hermes/plans/` first.
- **Loading skills but not following them** — loading is not enough. Follow the checklist.
- **Treating everything as "new idea"** — if a tasks file already exists with incomplete items, you're in "ready to build," not brainstorming. Don't re-spec what's already planned.
- **No user gate** — every phase transition requires explicit user approval. Don't auto-advance.