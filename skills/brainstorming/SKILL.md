---
name: brainstorming
description: "Use before any creative work — features, components, functionality, or behavior changes. Extracts specs through Socratic questioning before implementation. Pairs with writing-plans."
version: 1.0.0
author: dank0296 (adapted from obra/superpowers by Jesse Vincent)
license: MIT
metadata:
  hermes:
    tags: [planning, design, spec, brainstorming, methodology]
    related_skills: [writing-plans, plan, subagent-driven-development]
---

# Brainstorming Ideas Into Designs

Turn rough ideas into fully formed specs through natural collaborative dialogue. You are a Socratic design partner — extract clarity before anyone writes code.

## Hard Gate

**Do NOT write code, scaffold projects, or invoke implementation skills until a design has been presented and approved.** Every project goes through this, regardless of perceived simplicity. "Simple" projects are where unexamined assumptions cause the most wasted work. The design can be short (a few sentences for truly small things), but you MUST present it and get approval.

## Checklist

Work through these in order:

1. **Explore project context** — check existing files, git status, recent commits, AGENTS.md
2. **Scope check** — if the request describes multiple independent subsystems, flag it and help decompose before designing
3. **Ask clarifying questions** — one at a time, understand purpose/constraints/success criteria
4. **Propose 2-3 approaches** — with trade-offs and your recommendation
5. **Present design sections** — validated incrementally, one section at a time
6. **Write spec** — save to `.hermes/plans/YYYY-MM-DD-<topic>-spec.md`
7. **Spec self-review** — scan for placeholders, contradictions, ambiguity, scope creep
8. **User reviews spec** — gate: do not proceed until user approves
9. **Transition** — invoke the `writing-plans` skill to create the implementation plan

## Process Flow

```
Explore context → Scope check → Ask questions (one at a time)
    ↓
Propose 2-3 approaches → Recommend one
    ↓
Present design sections → User validates each
    ↓
Write spec → Self-review → User approves?
    ↓ YES
Invoke writing-plans skill
    ↓ NO — loop back to revise
```

## The Process

### Understanding the idea

- Check the current project state first (files, docs, recent commits)
- **Scope gate:** if the request describes multiple independent subsystems (e.g. "build a platform with chat, file storage, billing, analytics"), flag this immediately. Help decompose into sub-projects — what are the pieces, how do they relate, what order should they be built? Then brainstorm the first sub-project. Each sub-project gets its own spec → plan → implementation cycle.
- Ask questions one at a time. Only one question per message. If a topic needs more, break it into multiple questions.
- Prefer multiple choice when possible — easier to answer than open-ended.
- Focus on: purpose, constraints, success criteria, non-goals.

### Exploring approaches

- Propose 2-3 approaches with trade-offs.
- Lead with your recommendation and explain why.
- Frame options concretely: "Option A (recommended): Flask + SQLite — simplest, fastest to build. Option B: FastAPI + Postgres — more scalable but 2x setup time. Option C: Serverless — cheapest at low traffic but cold start latency."

### Presenting the design

- Once the approach is chosen, present the design in sections.
- Scale each section to its complexity — a few sentences if straightforward, 200-300 words if nuanced.
- Ask after each section: "Does this look right so far?"
- Cover: architecture, components/modules, data flow, error handling, testing strategy, file structure.
- Be ready to loop back if something doesn't land.

### Design for isolation

- Break the system into units with one clear purpose each, communicating through well-defined interfaces.
- For each unit: what does it do? How do you use it? What does it depend on?
- Can someone understand it without reading internals? Can you change internals without breaking consumers?
- Smaller, well-bounded units are easier for you and subagents to work with — you reason better about code you can hold in context at once.

### Working in existing codebases

- Explore the current structure before proposing changes. Follow existing patterns.
- Where existing code has problems that affect the work (overgrown files, unclear boundaries), include targeted improvements as part of the design. A good developer improves code they're working in.
- Do NOT propose unrelated refactoring. Stay focused on what serves the current goal.

## After the Design

### Documentation

Write the validated spec to `.hermes/plans/YYYY-MM-DD-<topic>-spec.md`. If the project has a preferred spec location in AGENTS.md, use that instead. Commit the spec document.

### Spec self-review

After writing, review with fresh eyes:

1. **Placeholder scan** — any "TBD", "TODO", incomplete sections? Fix them.
2. **Internal consistency** — do any sections contradict each other?
3. **Scope check** — is this focused enough for one implementation plan, or does it need decomposition?
4. **Ambiguity check** — could any requirement be interpreted two ways? Pick one and make it explicit.

Fix issues inline. No need to re-review — just fix and move on.

### User review gate

After self-review passes, present the spec:

> "Spec written to `.hermes/plans/<date>-<topic>-spec.md`. Please review and let me know if you want changes before I build the implementation plan."

Wait for the user. If they request changes, make them and re-run self-review. Only proceed once approved.

### Transition to implementation

Invoke the `writing-plans` skill to create the implementation plan. Do NOT invoke any other implementation skill. `writing-plans` is the only next step.

## Key Principles

- **One question at a time** — don't overwhelm with multiple questions
- **Multiple choice preferred** — easier to answer than open-ended
- **YAGNI ruthlessly** — remove unnecessary features from all designs
- **Explore alternatives** — always propose 2-3 approaches before settling
- **Incremental validation** — present design sections, get approval before moving on
- **Be flexible** — go back and clarify when something doesn't make sense
- **Start small** — if the project is large, decompose and brainstorm the first piece

## Pitfalls

- **Jumping to code** — the gate exists because agents default to writing code. Fight the instinct. Design first.
- **Over-questioning** — if the user clearly knows what they want, don't drag it out. Two good questions are better than eight filler questions.
- **Skipping alternatives** — even when one approach is obvious, articulating why it beats alternatives builds user confidence and catches blind spots.
- **Designing in isolation** — always check the existing codebase first. A beautiful design that ignores existing patterns creates more problems than it solves.