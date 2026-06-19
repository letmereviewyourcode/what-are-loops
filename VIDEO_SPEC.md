# VIDEO_SPEC.md — "What Are Loops" (LinkedIn motion graphic)

> Build target for Claude Code. Invoke with the short `/goal` at the bottom of this file.
> Source of truth: this spec. If anything here is ambiguous, prefer the simplest reading that satisfies the Definition of Done.
>
> **v2 (2026-06-19) — shipped.** Recut from the original 27s to **~58s / 1740 frames** per the creator's direction: each platform now gets a deliberate beat, `GOAL_TEXT` is typed **inside each tool's real input box**, two new teaching scenes were added (a "what a loop is" primer and a two-axes deep-dive), the presenter photo (`zishan.png`) appears as an intro lower-third and a circular sign-off, and the closer ends on a verify-recap. Frame ranges below reflect v2. `CAPTION_SCRIPT.md` holds the authoritative scene/word list.

---

## 1. Objective & message

A ~27-second motion graphic for LinkedIn that makes ONE point:

> Every major agentic coding tool has converged on the same "loop" primitive — they all now ship a `/goal`-style command — and the real differentiator is **how each verifies the work is done**. Autonomy is table stakes; verification is the moat.

Audience: technical + GTM people on LinkedIn. Must read with **sound OFF** (LinkedIn autoplays muted) — all narration is on-screen text, large and legible on mobile. Tone: confident, technical, clean. No cheesy effects, no fake data.

The "education" feel to emulate (clean conceptual figures, one idea each, crisp mental-model contrasts) is inspired by OpenAI's "Using Goals in Codex" cookbook — **inspired by, never copied**. See §9.

---

## 2. Assets (the user's own screenshots)

Source folder (already on disk):
`./Screenshots/`

Step 1 — after scaffolding the Remotion project, copy the USED assets into `public/`:

```
cp "./Screenshots/claude-goal.png" "./public/"
cp "./Screenshots/codex-goal.png" "./public/"
cp "./Screenshots/antigravity-goal.png" "./public/"
cp "./Screenshots/claude-routines.png" "./public/"
```

Load them with `staticFile('claude-goal.png')`, etc.

| File | Tool / state | Used in |
|---|---|---|
| `claude-goal.png` | Claude Code terminal, `/goal` in the slash menu ("Set a goal Claude checks before stopping") | Scene 2 |
| `codex-goal.png` | OpenAI Codex composer with `/goal` typed | Scene 3 |
| `antigravity-goal.png` | Google Antigravity 2.0 slash menu (`goal`, `schedule` visible) | Scene 4 |
| `claude-routines.png` | Claude Code Routines page | Scene 5 (inset) |
| `claude-code-web-version.png` | SPARE — a Claude cloud shot. Optional; not required. | — |
| `codex-goal-template.png` | REFERENCE ONLY — do **not** embed (see §9). Re-typeset its idea as our own graphic. | Scene 3 (recreated) |
| `Me - Zishan/linkedin_image_2026.png` → `public/zishan.png` | Creator's own headshot (presenter). | Primer lower-third + closer sign-off |

Note: these screenshots are mixed light/dark themes. Do **not** show them full-bleed. Frame each inside a rounded "window card" (see §4) floating on the dark stage so the themes don't clash and so they can shrink into the grid in Scene 5.

---

## 3. Global settings

- Two compositions, same scenes/components:
  - `LoopsVertical` — 1080 × 1350 (4:5, primary for LinkedIn feed)
  - `LoopsSquare` — 1080 × 1080 (1:1, alternate)
- `fps = 30`, `durationInFrames = 1740` (~58s). *(v2 — recut from 810/27s.)*
- Dark stage. Safe margin ≥ 64px on all sides.

---

## 4. Design system

- Background (stage): `#0B0B0C`. Window-card surface: `#161618`, 1px border `#2A2A2E`, radius 16, soft shadow.
- Text: `#F2F2F0` primary, `#9C9A92` muted/ghost hints.
- Accent (use sparingly): amber `#EF9F27` for the `/goal` keyword + the "Verification is the moat." line. Teal `#1D9E75` for non-Claude tools in the map.
- Fonts (via `@remotion/google-fonts`): headlines `Inter` (weight 500–600); command/mono text `JetBrains Mono`.
- Type sizes (1080-wide canvas): headline ≥ 44px, body/hint ≥ 28px, captions ≥ 28px.
- Motion: `spring()` for entrances; `interpolate()` + `Easing.bezier` for camera zoom/translate. Scene transitions = 8–12 frame scale+opacity blends, not hard cuts. No bounce overload.
- Window card: a centered rounded card holding one screenshot, scaled to ~85% canvas width in scenes 2–4. Optional 3-dot title bar. This card is the unit that shrinks into the 2×2 grid in Scene 5.

---

## 5. The `/goal` text (define ONCE, reuse everywhere)

```
const GOAL_TEXT = "/goal cut p95 checkout latency under 120ms, verified by the benchmark, with all tests green";
```

Type `GOAL_TEXT` character-by-character — the **same string in all three tool scenes**. Typing the identical command across three different products IS the convergence payoff; never vary it per tool. Highlight the `/goal` token in amber.

---

## 6. Storyboard (frames @ 30fps) — v2

### Scene 1 — Hook (0–150)
- Center headline rises + fades in: **"He stopped writing code."**
- Beat (~frame 50), second line slides under it: **"He writes loops."** (accent "loops").
- Small attribution, lower: *"— Boris Cherny, creator of Claude Code"*

### Scene 1.5 — What a loop IS · primer (150–300) [NEW, original graphic]
- Headline: **"A loop is an agent that runs itself."**
- Cycle graphic `generate → run → check → repeat` with a loop-back arc and a step highlight that cycles.
- Sub: *"no human in the inner loop — it keeps going on its own."*
- Presenter lower-third: circular `zishan.png` + **"Zishan Ali"** + *"mapping the agentic-coding loop"*.

### Scene 2 — Claude Code `/goal` (300–480)
- `claude-goal.png` window card, with a call-out: **"Claude Code"** + *"/goal · /loop · cloud Routines"*.
- Caret blink → highlight slides onto the "/goal — Set a goal Claude checks before stopping" row → the menu closes and `GOAL_TEXT` types **into the terminal input box** (`/goal` amber). Dim the "2 setup issues: MCP" line. Gentle push-in.
- Ghost hint: *"a separate model confirms it's done"*.

### Scene 3 — OpenAI Codex `/goal` + anatomy (480–690)
- `codex-goal.png` window card. Call-out: **"OpenAI Codex"** + *"Goal mode — now GA"*.
- `GOAL_TEXT` types **into the composer input box** (+ glyph, send button); push-in then ease back.
- **"anatomy of a goal"** reveal (ORIGINAL graphic — recreate, do not copy any cookbook figure): 3 chips with leader lines:
  - outcome → "p95 < 120ms" · verified by → "the benchmark" · constraint → "tests stay green"
- Caption: *"a finish line + proof + a guardrail = a goal, not a prompt."*

### Scene 4 — Google Antigravity `/goal` (690–870)
- `antigravity-goal.png` window card. Call-out: **"Google Antigravity 2.0"** + *"/goal · /schedule"*. Model chip: "Gemini 3.5 Flash".
- Highlight slides onto the existing `goal  Run until the specified goal is completely finished` menu row (already in the screenshot) → `GOAL_TEXT` types **into the composer input box** below it (blue send). Slight zoom.
- Ghost hint: *"verifies via artifacts you can audit"*.

### Micro-beat — prompt vs goal (870–1020) [education beat]
- ORIGINAL graphic. Line A: `Prompt:  ask → work → result → wait`; Line B morphs under it: `Goal:  work → check → continue / complete`.
- Punch (amber on the word): *"and 'done' is decided by evidence, not vibes."*

### Scene 4.5 — Two questions / the axes (1020–1230) [NEW, original graphic]
- Headline: **"Two questions define any loop."**
- Q1 *what makes it take the next step?* → **"Gated by a trigger"** ↔ **"Gated by verification"** (accented).
- Q2 *where does it live?* → **"In-session"** ↔ **"Cloud-persistent"**.
- Lead-in: *"Plot every tool on these two axes ↓"* — sets up the map's axes.

### Scene 5 — The map (1230–1500)
- 2×2 map. Axes: horizontal **"Gated by a trigger → Gated by verification"**; vertical **"In-session → Cloud-persistent"**.
- Pills pop into quadrants in sequence (Claude = amber, other tools = teal):
  - top-left (cloud + trigger): `Routines` (inset `claude-routines.png`), `Cursor Automations`, `Antigravity /schedule`
  - top-right (cloud + verification): `Codex Goal mode`, `Antigravity /goal`
  - bottom-left (in-session + trigger): `/loop`
  - bottom-right (in-session + verification): `/goal`
- Caption: **"Same loop. Shipped by 4 labs. In months."**

### Scene 6 — Thesis + verify-recap + CTA (1500–1740)
- smaller: "Autonomy is table stakes." → big, amber: **"Verification is the moat."**
- Verify-recap (original graphic) — *how each proves "done"*: Claude /goal → judge model · Codex Goal mode → tests until green · Antigravity /goal → audited artifacts · Routines / triggers → a trigger fires.
- Circular `zishan.png` sign-off. Lower third: "Zishan Ali · linkedin.com/in/zishanalikhan" and *"Which loop are you running?"*

---

## 7. Technical implementation (Remotion)

- Scaffold if no project exists: `npm create video@latest -- --template blank` at the repo root. If a Remotion project already exists here, extend it.
- Register both compositions in `src/Root.tsx` (or equivalent), sharing one `<LoopsVideo />` that takes the dimensions/format as props or reads `useVideoConfig()`.
- Suggested components:
  - `<TitleCard>` — headline + sub + attribution (Scenes 1, 6, micro-beat).
  - `<WindowCard src label dim?>` — frames a screenshot; handles the zoom and the shrink-to-grid.
  - `<TypeLine text start cps accentToken>` — frame-driven typing: `visible = Math.floor((frame - start) / framesPerChar)`; blinking caret after last char; render `/goal` token in amber.
  - `<AnatomyCallout>` — the 3 chips + leader lines (Scene 3).
  - `<FlowContrast>` — the prompt-vs-goal micro-beat.
  - `<QuadrantMap>` — the 2×2 with 7 pills on the two axes (mirror the agreed layout).
  - `<ThesisCard>` — Scene 6.
- Continuous camera: wrap Scenes 2–5 in a `<Camera>` that maps the global frame to a single scale/translate timeline via `interpolate`, so the Scene 5 pull-back reads as one move rather than a cut. Use `<Series>` or sequential `<Sequence>` for scene timing.
- Respect `prefers-reduced-motion` is not applicable in render, but keep motion smooth (no jank): animate only `transform`/`opacity`.

---

## 8. Build & render commands (put in repo README)

```
# install (after scaffold)
npm install

# copy assets into public/
cp "./Screenshots/claude-goal.png" "./Screenshots/codex-goal.png" "./Screenshots/antigravity-goal.png" "./Screenshots/claude-routines.png" "./public/"

# preview
npx remotion studio

# render (high quality h264)
npx remotion render LoopsVertical out/loops-vertical.mp4 --codec=h264 --crf=18
npx remotion render LoopsSquare   out/loops-square.mp4   --codec=h264 --crf=18
```

---

## 9. Copyright guardrails (non-negotiable)

- Only the user's own screenshots (`claude-goal`, `codex-goal`, `antigravity-goal`, `claude-routines`) may appear as real UI.
- Do **not** download, embed, screenshot, or trace any OpenAI / Anthropic / Google copyrighted images, docs figures, or marketing assets.
- `codex-goal-template.png` is the cookbook's template block — do **not** embed it. Re-typeset the goal scaffold in our own styling if shown at all.
- The "anatomy of a goal" chips and the prompt-vs-goal contrast are ORIGINAL graphics inspired by — not copied from — OpenAI's Goals guide.
- The fake-typed `GOAL_TEXT` is the user's own paraphrase, not a verbatim line from any source.

---

## 10. Definition of Done (verification surface for `/goal`)

The build is complete only when ALL of these are true:

1. `npm install` completes clean; `npx remotion studio` starts with no errors.
2. Two compositions registered: `LoopsVertical` (1080×1350) and `LoopsSquare` (1080×1080), both `fps=30`, `durationInFrames=1740`.
3. `./public/` contains the 4 used screenshots + `zishan.png` (presenter); every `<Img>` resolves (no missing-asset errors in studio).
4. All scenes present in order with the §6 frame ranges (±10 frames ok): Hook → loop primer → Claude → Codex+anatomy → Antigravity → prompt-vs-goal micro-beat → two-axes → map → thesis+recap.
5. `GOAL_TEXT` is a single shared constant, typed identically in Scenes 2, 3, and 4 — **inside each tool's input box** — with `/goal` highlighted.
6. The map shows all 7 pills on the trigger↔verification × in-session↔cloud axes, color-coded Claude vs other tools.
7. Captions ≥ 44px headline / ≥ 28px body; safe margins ≥ 64px; nothing clips in either composition.
8. No OpenAI/Anthropic/Google copyrighted figures embedded; `codex-goal-template.png` not used as an image. Only the creator's own screenshots + headshot appear.
9. `npx remotion render LoopsVertical out/loops-vertical.mp4 --codec=h264 --crf=18` produces a non-empty `.mp4` (> 1 MB, ~58s) with no render errors. Same for `LoopsSquare`.
10. Repo README documents the preview + render commands.

---

## /goal to run this spec

```
/goal Build the Remotion video defined in VIDEO_SPEC.md. Verified by: every item in section 10 (Definition of Done) is satisfied — npx remotion studio runs error-free, both compositions render to non-empty mp4s via the section 8 commands, and only my own screenshots are used. Use only this repo and its ./Screenshots assets. After each iteration, check the work against section 10 and fix the first failing item. If a render fails or an asset is missing, stop and report the exact blocker and what would unlock it.
```
