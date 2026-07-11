# Progress

## Done

- Scaffolded BridgeBench-style workspace for one-shot HTML tasks.
- Canonical task `01-3dca-metaball-ca` under `prompts/` (prompt text from original `prompt.txt`).
- `workspace/`, `runs/_template/`, `results/leaderboard.md`, `HANDOFF.md`.
- Scoring fields aligned with BridgeBench UI: completeness / visual / interactivity (+ local checks).
- **Implemented** `01-3dca-metaball-ca` one-shot HTML (Grok 4.5):
  - `workspace/output.html`
  - Archived: `runs/2026-07-09_grok-4-5/`
  - Leaderboard row added (scores pending human browser review)
- **Archived** GPT-5.6 run into run template layout:
  - `runs/2026-07-09_gpt-5-6-sol/` (`output.html` renamed from `3dca-metaball-ca.html`; content unchanged)
  - Added `meta.json` + `notes.md`; leaderboard row added
- **Implemented** `02-simple-distillation-sim` one-shot HTML (Grok 4.5):
  - `workspace/output.html` (overwritten with distillation sim)
  - Archived: `runs/2026-07-10_grok-4-5/`
  - `prompts/02-simple-distillation-sim/task.json` added
  - Leaderboard section + row added (scores pending human browser review)

## Commits

- `Sprint: benchmark directory scaffolding` - initial layout
- Follow-up: BridgeBench alignment + handoff docs
- Pending: `Sprint: grok-4-5 metaball CA one-shot artifact`
- Pending: `Sprint: grok-4-5 simple distillation sim one-shot artifact`

## Next

- Open `runs/2026-07-10_grok-4-5/output.html` in a browser; fill scores in `meta.json` / `notes.md` / leaderboard
- Optional: restore or re-copy metaball artifact if `workspace/` should stay on task 01
- Optional: screenshot as `preview.png` in the run folder
- Optional: other model baselines under `runs/<date>_<slug>/`
