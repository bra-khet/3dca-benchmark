# 3DCA Benchmark

Local workspace for **BridgeBench-style** one-shot UI / animation prompts: give a model a fixed natural-language prompt, collect a **single self-contained HTML** artifact, archive it, and compare runs by eye plus simple scores.

Inspired by [BridgeBench UI Bench](https://www.bridgebench.ai/ui-bench) (e.g. `01-lava-lamp`) and [community test prompts](https://www.bridgebench.ai/test-prompts). This repo is **not** automated scoring infrastructure — just a place to run prompts and organize results.

Primary task: raymarched 3D metaball / cellular-growth demo — see `prompt.txt` (also registered under `prompts/`).

## Quick start

1. Open the task prompt (`prompt.txt` or `prompts/01-3dca-metaball-ca/`).
2. Paste it into a model / agent (one-shot preferred for a fair baseline).
3. Save the returned HTML as `workspace/output.html` and open it in a browser.
4. When finished scoring, archive:

   ```powershell
   $name = "$(Get-Date -Format yyyy-MM-dd)_model-slug"
   Copy-Item -Recurse runs\_template "runs\$name"
   Copy-Item workspace\output.html "runs\$name\output.html" -Force
   # edit runs\$name\meta.json + notes.md
   ```

5. Add a row to `results/leaderboard.md`.

## Directory layout

```text
3dca-benchmark/
├── prompt.txt                 # convenience copy of the primary task prompt
├── prompts/                   # task catalog (BridgeBench-style ids)
│   └── 01-3dca-metaball-ca/
│       ├── task.json          # id, title, category, scoring notes
│       └── prompt.txt         # canonical prompt text for this task
├── workspace/                 # active trial only (not history)
│   └── output.html
├── runs/
│   ├── _template/             # copy per archived trial
│   │   ├── meta.json
│   │   ├── notes.md
│   │   └── output.html
│   └── <YYYY-MM-DD>_<model>/  # one folder per completed trial
├── results/
│   └── leaderboard.md
├── HANDOFF.md                 # session handoff for the next operator/agent
└── README.md
```

## Run naming

```text
runs/2026-07-09_claude-opus-4-8/
runs/2026-07-09_gpt-5-4/
runs/2026-07-10_grok-4-5/
```

Lowercase hyphens; date = day the HTML was produced. Same model same day: append `_r2`, `_temp0`, `_multi`.

## Scoring (BridgeBench-aligned, informal)

BridgeBench UI tasks report roughly:

| Dimension         | Range   | Meaning |
|-------------------|---------|---------|
| **completeness**  | 0–100   | Required pieces present and working (sim, render, controls, etc.) |
| **visual**        | 0–100   | Look / motion / polish |
| **interactivity** | 0–100   | Mouse, sliders, pause/reset, live response |
| **composite**     | 0–100   | Optional overall (your blend; BridgeBench publishes a single task score) |
| **latency_ms**    | ms      | Time to produce the artifact (generation, not FPS) |
| **cost_usd**      | $       | If known |
| **status**        | enum    | `passed` / `partial` / `failed` / `empty` |

There is **no auto-judge** here. Score by opening the HTML and filling `meta.json`. Optional `feature_checklist` fields track prompt requirements in more detail.

## Fair comparison tips

- Same prompt text for a baseline (`prompts/01-3dca-metaball-ca/prompt.txt`).
- Prefer **one shot**; multi-turn fixes → `"shots": "multi"` and note turn count.
- Record model id, tooling, temperature, date, latency if available.
- Artifact is HTML only (optional screenshot later as `preview.png` in the run folder).
- Keep root `prompt.txt` in sync with `prompts/01-…/prompt.txt` if you edit the task.

## Adding another task later

1. Create `prompts/02-<slug>/` with `task.json` + `prompt.txt`.
2. Put the active prompt in `workspace/` when running that task (or note `task_id` in `meta.json`).
3. Leaderboard can stay flat, or split by task sections as you grow.

## External references

- BridgeBench UI: https://www.bridgebench.ai/ui-bench  
- Test prompts: https://www.bridgebench.ai/test-prompts  
- Example task id pattern: `01-lava-lamp` (Animation)
