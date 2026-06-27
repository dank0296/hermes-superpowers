# ⚡ Hermes Superpowers — YouTube Short Storyboard

**Channel:** @DankAI  
**Length:** 60 seconds  
**Hook:** "Most coding agents fail because they jump straight to code."

---

## SHOT 1 — The Fail (0:00 – 0:05)

| Element | Detail |
|---------|--------|
| **Visual** | Hermes terminal, user types "Build a REST API for user auth" |
| **Action** | Agent immediately starts writing code — messy, no structure, creates 3 files at once |
| **Overlay** | ❌ No spec ❌ No plan ❌ No tests |
| **Audio** | "Most coding agents do this. You ask for a feature, they just... start typing." |
| **Caption** | **90% OF CODING AGENTS FAIL HERE** |

---

## SHOT 2 — The Hook (0:05 – 0:12)

| Element | Detail |
|---------|--------|
| **Visual** | Split screen — left: chaos from Shot 1, right: clean spec doc |
| **Action** | Right side loads hermes-superpowers skill |
| **Overlay** | Phase: New Idea → brainstorming |
| **Audio** | "Here's what happens when you force it to think first." |
| **Caption** | **SPEC-FIRST DEVELOPMENT ↓** |

---

## SHOT 3 — Brainstorming (0:12 – 0:22)

| Element | Detail |
|---------|--------|
| **Visual** | Terminal — agent asks questions ONE AT A TIME |
| **Action** | "JWT or sessions?" → "What database?" → "Rate limiting needed?" |
| **Overlay** | Question 1/3 → 2/3 → 3/3 |
| **Audio** | "It asks questions. One at a time. Extracts what you actually need." |
| **Caption** | **ONE QUESTION AT A TIME. NO ASSUMPTIONS.** |

---

## SHOT 4 — The Spec (0:22 – 0:30)

| Element | Detail |
|---------|--------|
| **Visual** | Terminal showing spec file being written to `.hermes/plans/auth-api-spec.md` |
| **Action** | Quick scroll through spec sections: architecture, data flow, error handling |
| **Overlay** | ✅ Spec approved |
| **Audio** | "You approve the design in sections. Nothing gets built until you say yes." |
| **Caption** | **GATE: USER MUST APPROVE BEFORE CODE** |

---

## SHOT 5 — The Plan (0:30 – 0:40)

| Element | Detail |
|---------|--------|
| **Visual** | writing-plans skill breaks spec into 6 tasks |
| **Action** | Tasks appear one by one: "1. User model + migration (3 min)", "2. JWT middleware (4 min)", etc. |
| **Overlay** | 6 tasks · 22 min estimated |
| **Audio** | "Then it writes a plan. Bite-sized tasks. Exact file paths. Every task under 5 minutes." |
| **Caption** | **BITE-SIZED TASKS → SUBAGENTS** |

---

## SHOT 6 — Subagents Execute (0:40 – 0:50)

| Element | Detail |
|---------|--------|
| **Visual** | Split terminal — 3 subagents running in parallel via delegate_task |
| **Action** | Subagent 1 builds models, Subagent 2 builds middleware, Subagent 3 builds routes |
| **Overlay** | ⚡ Parallel execution · 3 subagents |
| **Audio** | "Subagents execute in parallel. Each gets isolated context. Two-stage review between batches." |
| **Caption** | **3 SUBAGENTS · PARALLEL · AUTONOMOUS** |

---

## SHOT 7 — All Green (0:50 – 0:56)

| Element | Detail |
|---------|--------|
| **Visual** | Terminal — all checks pass, all tasks ✅ |
| **Action** | "All 6 tasks complete. Tests passing. Merge to main? [y/n]" |
| **Overlay** | ✅ 6/6 tasks · ✅ All tests pass |
| **Audio** | "It works autonomously for hours without deviating from the plan." |
| **Caption** | **AUTONOMOUS. ON-PLAN. NO DRIFT.** |

---

## SHOT 8 — CTA (0:56 – 1:00)

| Element | Detail |
|---------|--------|
| **Visual** | GitHub repo README on screen + QR code |
| **Action** | Zoom out to show repo URL |
| **Overlay** | github.com/dank0296/hermes-superpowers |
| **Audio** | "Skills in the repo. Link in description. Spec-first. Always." |
| **Caption** | **⚡ HERMES SUPERPOWERS — LINK IN BIO** |

---

## Production Notes

- **Music:** Electronic, 25% volume. Beat drops at 0:05 (shot 2 transition).
- **Recording:** Hermes terminal with dark theme. 1080×1920 vertical crop.
- **Tool:** `asciinema` for clean terminal recording, then crop to vertical in CapCut/DaVinci.
- **Source audio:** Record voiceover separately, sync in post.
- **Assets needed:** Hermes terminal recording of the full brainstorming → spec → plan → subagents flow.

## CTA on Screen

| Element | Content |
|---------|---------|
| Comment | "What's your coding agent's worst habit?" |
| Description | Skills, repo link, Hermes install instructions |
| Pinned comment | Timestamps + "Phase you're stuck on?" |

---

## Script (for voiceover)

```
Most coding agents do this. You ask for a feature, they just start typing.
No spec. No plan. No tests.

Here's what happens when you force it to think first.

It asks questions. One at a time. Extracts what you actually need.
You approve the design in sections. Nothing gets built until you say yes.

Then it writes a plan. Bite-sized tasks. Exact file paths. Every task under five minutes.

Subagents execute in parallel. Each gets isolated context. Two-stage review between batches.

It works autonomously for hours without deviating from the plan.

Skills in the repo. Link in description. Spec-first. Always.
```