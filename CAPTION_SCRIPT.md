# CAPTION_SCRIPT.md — exact on-screen text, timing & verification

> Pairs with `VIDEO_SPEC.md`. The spec owns layout/assets/build; this file owns the words, the timing, and how we verify the result. 30 fps, **1740 frames (~58s)**.
>
> **v2 (2026-06-19):** recut from the original 27s per the creator's direction — slower per-platform beats, an in-box typing treatment (the command is typed *inside* each tool's real input box), a "what a loop is" primer, a two-axes deep-dive, a presenter photo, and a verify-recap closer. All **[LOCKED]** strings below are unchanged.

---

## How to read this

- **[LOCKED]** = this exact string must appear, verbatim. Don't reword.
- **[FREE]** = Claude Code's call — style, animate, retime, or improve it; keep the meaning.
- Frame ranges are targets (±10 frames fine). Timing is **[FREE]** to refine for rhythm as long as scene order and the locked copy are intact.

---

## Creative liberty — what's locked vs yours

**Locked (do not change):**
- The thesis and message (convergence on the loop → verification is the differentiator).
- All **[LOCKED]** strings below, verbatim.
- `GOAL_TEXT` identical across the three tool scenes.
- Accuracy + copyright guardrails (VIDEO_SPEC §9): only my own screenshots; no OpenAI/Anthropic/Google figures; `codex-goal-template.png` never embedded.
- The 7 pills and the two axes in the map.
- Definition of Done (VIDEO_SPEC §10) + the verification layers below.

**Yours (use it well):**
- All motion: easing, springs, caret/typing feel, highlight sweeps, transitions, parallax, push-ins.
- Exact frame timings, hold durations, and pacing.
- Visual polish within the design system; the new primer / two-axes / verify-recap graphics; presenter photo placement.
- Tasteful beats that *serve* the message — but never fake output, metrics, or behavior a tool doesn't have.

---

## Full caption script

### Scene 1 — Hook · frames 0–150
- `He stopped writing code.` **[LOCKED]** — in ~10. Rises + fades.
- `He writes loops.` **[LOCKED]** — in ~50. Accent the word "loops".
- `— Boris Cherny, creator of Claude Code` **[LOCKED]** — in ~72, muted, smaller.

### Scene 1.5 — What a loop IS (primer) · frames 150–300 **[FREE — original graphic]**
- Headline: `A loop is an agent that runs itself.` — accent "runs itself".
- Cycle graphic: `generate → run → check → repeat`, with a loop-back arc and a step highlight that cycles (it keeps going on its own).
- Sub: `no human in the inner loop — it keeps going on its own.`
- Presenter intro (photo): `Zishan Ali` + `mapping the agentic-coding loop` — small circular avatar, lower.

### Scene 2 — Claude Code · frames 300–480
- Label `Claude Code` **[LOCKED]** — call-out + window-card title. Descriptor `/goal · /loop · cloud Routines` **[FREE]**.
- Caret blink → highlight the `/goal — Set a goal Claude checks before stopping` suggestion row → the menu closes and `GOAL_TEXT` **[LOCKED]** types **into the terminal input box**. `/goal` token in amber.
- Ghost hint: `a separate model confirms it's done` **[LOCKED]** — muted, after typing.

### Scene 3 — OpenAI Codex + anatomy · frames 480–690
- Label `OpenAI Codex` **[LOCKED]**. Descriptor `Goal mode — now GA` **[FREE]**.
- `GOAL_TEXT` **[LOCKED]** types **into the composer input box** (+ glyph, send button).
- Anatomy chips (original graphic), leader lines to the matching words:
  - `outcome` → `p95 < 120ms` **[LOCKED pairing]**
  - `verified by` → `the benchmark` **[LOCKED pairing]**
  - `constraint` → `tests stay green` **[LOCKED pairing]**
- Caption: `a finish line + proof + a guardrail = a goal, not a prompt.` **[LOCKED]**

### Scene 4 — Google Antigravity 2.0 · frames 690–870
- Label `Google Antigravity 2.0` **[LOCKED]**. Model chip `Gemini 3.5 Flash` **[FREE]**. Descriptor `/goal · /schedule` **[FREE]**.
- Highlight the existing menu row in the image: `goal — Run until the specified goal is completely finished` — **don't retype that row; it's already in the screenshot.** Then `GOAL_TEXT` **[LOCKED]** types **into the composer input box** below it (blue send button).
- Ghost hint: `verifies via artifacts you can audit` **[LOCKED]** — muted.

### Micro-beat — what a loop IS · frames 870–1020
- `Prompt:  ask → work → result → wait` **[LOCKED]** — in ~5.
- `Goal:  work → check → continue / complete` **[LOCKED]** — in ~40, morph/replace from the line above.
- Punch: `and "done" is decided by evidence, not vibes.` **[LOCKED]** — accent "evidence".

### Scene 4.5 — Two questions (the axes) · frames 1020–1230 **[FREE — original graphic]**
- Headline: `Two questions define any loop.`
- Q1 `what makes it take the next step?` → `Gated by a trigger` **[LOCKED]** (a schedule or an event fires it) ↔ `Gated by verification` **[LOCKED]** (runs until a goal is met & proven, accented).
- Q2 `where does it live?` → `In-session` **[LOCKED]** (ends when you close it) ↔ `Cloud-persistent` **[LOCKED]** (survives a closed laptop).
- Lead-in: `Plot every tool on these two axes ↓`

### Scene 5 — The map · frames 1230–1500
- Axis labels **[LOCKED]**: `Gated by a trigger` · `Gated by verification` · `In-session` · `Cloud-persistent`.
- Pills appear in sequence **[LOCKED text, FREE order/animation]**:
  - top-left (cloud + trigger): `Routines` · `Cursor Automations` · `Antigravity /schedule`
  - top-right (cloud + verification): `Codex Goal mode` · `Antigravity /goal`
  - bottom-left (in-session + trigger): `/loop`
  - bottom-right (in-session + verification): `/goal`
  - Color: Claude pills one color, other tools another (match the legend).
- Caption: `Same loop. Shipped by 4 labs. In months.` **[LOCKED]**

### Scene 6 — Thesis + verify-recap + CTA · frames 1500–1740
- `Autonomy is table stakes.` **[LOCKED]** — smaller.
- `Verification is the moat.` **[LOCKED]** — big, amber.
- Verify-recap (original graphic) — `how each proves "done":` **[FREE]**
  - `Claude /goal → an independent judge model`
  - `Codex Goal mode → tests until green`
  - `Antigravity /goal → human-audited artifacts`
  - `Routines / triggers → a defined trigger fires`
- Presenter photo: circular avatar (amber ring).
- Lower third: `Zishan Ali · [your LinkedIn handle]` **https://www.linkedin.com/in/zishanalikhan/**.
- `Which loop are you running?` **[LOCKED]**

---

## Verification layers & acceptance criteria

Run these in order. Fix the **first** failing layer, then re-verify from Layer 0. (Yes — a verification loop, to build a video about verification loops.)

### Layer 0 — Build & static
- [ ] `npm install` clean; TypeScript compiles; no lint errors.
- [ ] `npx remotion studio` starts with no console errors.
- [ ] All `<Img>` resolve from `public/` (no missing-asset warnings).
- [ ] Both compositions registered: `LoopsVertical` 1080×1350, `LoopsSquare` 1080×1080, `fps=30`, `durationInFrames=1740`.

### Layer 1 — Frame stills (evidence, not vibes)
Render stills and confirm the expected **[LOCKED]** caption is visibly present, on-screen, inside safe margins:
```
npx remotion still LoopsVertical out/still-0090.png --frame=90     # "He stopped writing code."
npx remotion still LoopsVertical out/still-0280.png --frame=280    # "A loop is an agent that runs itself" + presenter
npx remotion still LoopsVertical out/still-0430.png --frame=430    # Claude Code + GOAL_TEXT typed in the terminal box
npx remotion still LoopsVertical out/still-0650.png --frame=650    # Codex composer typed + anatomy chips
npx remotion still LoopsVertical out/still-0800.png --frame=800    # Antigravity goal row highlighted + typed in box
npx remotion still LoopsVertical out/still-0950.png --frame=950    # prompt → goal contrast
npx remotion still LoopsVertical out/still-1130.png --frame=1130   # the two axes (trigger↔verification, session↔cloud)
npx remotion still LoopsVertical out/still-1380.png --frame=1380   # the 2x2 map populated
npx remotion still LoopsVertical out/still-1700.png --frame=1700   # "Verification is the moat." + verify-recap + presenter
```
- [ ] Each still shows the right scene + its locked text, legible, not clipped.

### Layer 2 — Content & accuracy
- [ ] `GOAL_TEXT` is one shared constant, typed identically in Scenes 2, 3, 4 — **inside each tool's input box**.
- [ ] All `[LOCKED]` strings present verbatim; anatomy pairings correct.
- [ ] Map has all 7 pills on the correct axes, color-coded Claude vs other tools.
- [ ] Only my own screenshots + my presenter photo used; no external copyrighted figures; `codex-goal-template.png` not embedded.

### Layer 3 — Full render
```
npx remotion render LoopsVertical out/loops-vertical.mp4 --codec=h264 --crf=18
npx remotion render LoopsSquare   out/loops-square.mp4   --codec=h264 --crf=18
```
- [ ] Both mp4s exist, non-empty (> 1 MB), render with no errors.
- [ ] Duration ≈ 58s (verify, e.g. `ffprobe -v error -show_entries format=duration -of csv=p=0 out/loops-vertical.mp4` → ~58.0).

### Acceptance
**Done = all four layers pass.** Report a short table of each layer's status and link the rendered files + the 9 stills. If anything fails, state which layer, fix the first failing item, and re-run from Layer 0.
