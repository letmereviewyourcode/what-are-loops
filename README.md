# What Are Loops — *Agents, Orchestrated · EP 01*

A ~58-second LinkedIn motion graphic on a pattern every agentic coding tool has quietly converged on: the **loop** — an agent that runs itself (generate → run → check → repeat). Claude Code, OpenAI Codex, and Google Antigravity all shipped the same `/goal`-style command, independently, within months. The take: **autonomy is table stakes; verification is the moat — the loop you can audit is the only one that ships.**

> **The meta part (why this repo exists):** I didn't hand-edit this video. I pointed a single Claude Code **`/goal`** at a spec — [`VIDEO_SPEC.md`](VIDEO_SPEC.md) + [`CAPTION_SCRIPT.md`](CAPTION_SCRIPT.md) — and it built the whole thing, then **verified itself frame-by-frame** (rendering stills and checking the right caption was actually on screen) before calling the job done. A verification loop, to make a video about verification loops. This repo is the **spec**, the **verification approach**, and a **deep-dive on the concept** — not the rendering code.

📺 The video lives on LinkedIn → https://www.linkedin.com/in/zishanalikhan/

---

## Start here

- **[`LOOPS_DEEP_DIVE.md`](LOOPS_DEEP_DIVE.md)** — the long version of the video: what a loop *is*, the four components every loop is built from, and **how each company (Claude Code · Codex · Antigravity · Cursor) does it right now**, with a side-by-side table. ← read this
- **[`VIDEO_SPEC.md`](VIDEO_SPEC.md)** — the exact spec I handed the `/goal`: objective, design system, storyboard, and the Definition of Done.
- **[`CAPTION_SCRIPT.md`](CAPTION_SCRIPT.md)** — every on-screen word + the **4-layer verification loop** that decides "done."

## What's inside

| Path | What it is |
|---|---|
| [`LOOPS_DEEP_DIVE.md`](LOOPS_DEEP_DIVE.md) | Field guide: the anatomy of a loop + how each tool implements it. |
| [`VIDEO_SPEC.md`](VIDEO_SPEC.md) | The build spec — and the `/goal` that runs it. |
| [`CAPTION_SCRIPT.md`](CAPTION_SCRIPT.md) | Locked on-screen copy, timing, and the 4-layer verification. |
| [`NARRATION.md`](NARRATION.md) · [`teleprompter.html`](teleprompter.html) | Voiceover script + a synced teleprompter for recording it on time. |
| `Screenshots/` | The real product captures — the only real third-party UI in the video (my own screenshots). |
| `out/loops-vertical.mp4` · `out/map-2x2.png` | The rendered video and the 2×2 map. |

> The Remotion implementation that renders all this is kept private — this repo is the spec + the deep-dive + the result.

## How "done" is decided (the 4-layer loop)

The build isn't finished when an `.mp4` exists — only when all four layers in [`CAPTION_SCRIPT.md`](CAPTION_SCRIPT.md) pass, in order:

0. **Build & static** — compiles clean, both compositions register, every asset resolves.
1. **Frame stills** — render a still per scene and confirm the *correct locked caption* is on screen, legible, not clipped (evidence, not vibes).
2. **Content & accuracy** — one shared `GOAL_TEXT` typed identically in all three tools, every locked string verbatim, the 7 map pills correct, only my own imagery.
3. **Full render** — both `.mp4`s render error-free, ~58 s, audio synced.

## Guardrails (non-negotiable)

Only my own screenshots and my own headshot appear as real imagery. The `/goal` command is typed into clean input fields laid exactly over each tool's real input box. **No OpenAI / Anthropic / Google copyrighted figures, docs, or marketing assets are embedded.** The conceptual graphics — the loop primer, the "anatomy of a goal," the prompt-vs-goal contrast, the two-axes map, the verify-recap — are original, *inspired by* OpenAI's Goals cookbook, never copied from it.

## Series

Part of **Agents, Orchestrated** — a weekly series on what makes agentic systems actually ship (not chatbot demos). Each episode pairs a broad-reach topic with a deep take on the control plane: verification, human-in-the-loop, governance, orchestration. *Autonomy is table stakes; the moat is everything around the agent.*
