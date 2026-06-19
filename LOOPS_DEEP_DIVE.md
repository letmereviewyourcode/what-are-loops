# The Agentic Loop — a Field Guide

> Companion to the EP 01 video ("What Are Loops"). The video makes one point in 58 seconds; this goes a level deeper: **what a loop actually is, the components every loop is built from, and how each major coding tool implements them right now.**
>
> *Scope & honesty:* this is a synthesis as of **early 2026**, grounded in each tool's own UI (the screenshots in this repo) and public behavior. These products ship fast — treat version-specific details as "true when written," and verify before quoting. Where something isn't nailed down, it's marked *(verify)*.

---

## TL;DR

A "loop" is an agent that runs itself — **generate → run → check → repeat** — with no human in the inner loop. Every major agentic coding tool converged on the same primitive (a `/goal`-style command) within months, independently. So the autonomy isn't the differentiator anymore. The differentiator is the part the video calls the moat: **how each loop decides it's actually done, and whether you can audit that decision.**

---

## Part 1 — What a loop is

A normal prompt is a single turn: you ask, the model works, you get a result, you wait. A **loop** closes that cycle and hands the steering wheel to the agent:

```
        ┌───────────────────────────────────┐
        ▼                                   │
   generate ──► run ──► check ──► (done?)  ─┘  no → keep going
                                    │
                                    └─ yes → stop
```

The agent generates work, runs/executes it, **checks the result against something**, and either continues or stops. The whole game is in that *check* — it's what separates a loop that grinds forever from one that knows when to quit, and it's where the four labs differ most.

---

## Part 2 — The components of a loop

Every loop, in every tool, is assembled from the same four parts.

### 1. The continuation driver — *what makes it take the next step*
Two answers in the wild:
- **A trigger** — a schedule or an event kicks the loop off and/or paces it ("every morning," "on every PR," "as a one-time timer"). The loop runs because *something fired*.
- **A goal** — the loop runs *until a target is verifiably met*. It continues because the work *isn't done yet*.

This is the horizontal axis of the map: **gated by a trigger ↔ gated by verification.**

### 2. The verification mechanism — *how "done" is decided* (the moat)
This is the component that matters. When the agent asks "am I done?", what answers? Four patterns:

| Pattern | "Done" means… | Trust comes from… |
|---|---|---|
| **Independent judge** | a *separate* model reviews the work and confirms it | a second opinion, not the worker grading itself |
| **Tests-until-green** | the defined tests pass | an objective, pre-agreed bar |
| **Human-audited artifacts** | a person can inspect what it produced | a reviewable paper trail |
| **A defined trigger** | the thing you scheduled ran | you decided the conditions up front |

The thesis of the whole episode: *when everything can loop, this column is the moat.* "Autonomy" is now table stakes; **the loop you can audit is the only one that ships** — and in regulated industries that's the entire game.

### 3. The goal itself — *a finish line + proof + a guardrail*
A goal is not a fancier prompt. The video's "anatomy of a goal" breaks it into three parts, and a real goal has all three:
- **Outcome** — the finish line (e.g., "p95 checkout latency under 120ms").
- **Verified by** — the proof it's met (e.g., "the benchmark").
- **Constraint** — the guardrail it must not break (e.g., "tests stay green").

> *outcome + proof + guardrail = a goal, not a prompt.*

A prompt asks for work and waits. A goal lets the agent check its own work and keep going — and "done" is decided by **evidence, not vibes.**

### 4. The locus — *where the loop lives*
- **In-session** — it runs in your terminal/editor; close the session and it ends.
- **Cloud-persistent** — it runs server-side and survives a closed laptop (scheduled jobs, background agents).

This is the vertical axis of the map: **in-session ↔ cloud-persistent.**

### The synthesis — the 2×2
Plot any tool's loops on *continuation driver* (×) and *locus* (y) and they all land on the same map (see `out/map-2x2.png`). The point isn't where the dots sit — it's that the **interesting differences are all on the right-hand, verification side.**

---

## Part 3 — How each tool does it right now

*Grounded in each tool's own UI (screenshots in `/Screenshots`) and public behavior, early 2026.*

### Claude Code (Anthropic)
- **`/goal`** — the in-session verification loop. Its own slash-menu describes it as *"Set a goal Claude checks before stopping."* The notable design choice: a **separate model confirms the work is actually done** rather than the working agent grading itself — the "independent judge" pattern. *(This whole video was built by pointing one `/goal` at a spec and letting it verify its own output frame-by-frame.)*
- **`/loop`** — in-session repeat/iterate.
- **Routines** — cloud-persistent, templated jobs that run on a schedule / via API / webhook (briefing, triage, PR review, etc.). Trigger-gated.
- *Map position:* `/goal` bottom-right (in-session + verification), `/loop` bottom-left, Routines top-left (cloud + trigger).

### OpenAI Codex
- **Goal mode** — now GA. You give it an outcome and it **runs the tests until they pass** — the "tests-until-green" verification pattern. Cloud-capable.
- *Map position:* Codex Goal mode top-right (cloud + verification).
- *Credibility note:* OpenAI's own Goals guide makes the same argument this video does — a task is done **when the evidence says so, not when the model thinks it's probably done.** That turns "verification is the moat" from one person's opinion into cross-lab consensus.

### Google Antigravity
- **`/goal`** — its slash-menu reads *"Run until the specified goal is completely finished."* Verification leans on **artifacts you can audit** (it produces inspectable outputs).
- **`/schedule`** — *"Run an instruction on a recurring schedule or as a one-time timer"* — the trigger/cloud-persistent side.
- Runs on a selectable model (the captured UI shows a Gemini model chip).
- *Map position:* Antigravity `/goal` top-right (cloud + verification), `/schedule` top-left (cloud + trigger).

### Cursor *(and the broader field)*
- **Automations** — cloud agents that run **on a schedule or in response to events** (GitHub, Slack, Linear, webhooks, PagerDuty…); each spins up a sandbox, follows your instructions, and **verifies its own output**. Trigger-gated and cloud-persistent → top-left (cloud + trigger). Cursor's own security team runs a fleet of these reviewing thousands of PRs a week.
- The pattern is wider than these four — other editors and agent frameworks are adding the same loop primitive. The point of the episode is the **convergence**, not an exhaustive census.

### Side-by-side

| Tool | Loop command(s) | Continuation driver | How "done" is decided | Locus |
|---|---|---|---|---|
| **Claude Code** | `/goal`, `/loop`, Routines | goal + trigger | independent judge model | in-session + cloud |
| **OpenAI Codex** | Goal mode | goal | tests-until-green | cloud |
| **Google Antigravity** | `/goal`, `/schedule` | goal + trigger | human-audited artifacts | cloud |
| **Cursor** | Automations | trigger (schedule / event) | self-verifies its output | cloud |

---

## Part 4 — Why verification is the moat

Autonomy used to be the hard part. It isn't anymore — every tool above can run itself. So the question that decides whether an agent ships stops being *"can it act on its own?"* and becomes *"how do I trust what it did?"* Each tool answers differently — an independent judge, tests-until-green, a defined trigger, human-audited artifacts — and **that answer is the product.**

For anyone in a regulated or high-stakes context, it's not even close: an autonomous loop you can't audit is a liability, not a feature. The loop you *can* audit is the only one that ships.

So — **which loop are you running?**

---

## Sources & further reading
- **OpenAI, "Using Goals in Codex"** — the official Goals guide; completion is evidence-based: *"A Goal should not be marked complete because the model believes it is probably done… the evidence decides whether it is done."* → https://developers.openai.com/cookbook/examples/codex/using_goals_in_codex
- **Cursor, "Automations"** — official docs; scheduled/event-triggered cloud agents that verify their own output → https://cursor.com/docs/cloud-agent/automations
- **Boris Cherny (creator of Claude Code), on writing loops instead of prompts** — *"I don't prompt Claude anymore. I have loops that are running."* → https://officechai.com/ai/i-now-just-write-loops-to-prompt-claude-code-claude-code-creator-boris-cherny/
- Each tool's own UI is captured in [`Screenshots/`](Screenshots/). Product specifics are as of **early 2026** and move fast — verify before quoting.

---

*Part of **Agents, Orchestrated** — a series on what makes agentic systems actually ship. Watch EP 01 (the 58-second video) for the short version; this guide is the long one. Spec for the video itself is in [`VIDEO_SPEC.md`](VIDEO_SPEC.md).*
