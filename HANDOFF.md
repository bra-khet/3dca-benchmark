# Handoff

## What this repo is

A **local, manual** workspace for BridgeBench-style creative HTML benchmarks:

1. Fixed prompt → one-shot (or noted multi-shot) model run  
2. Self-contained `output.html` artifact  
3. Archive under `runs/` with scores + notes  
4. Summarize in `results/leaderboard.md`

Primary task: **`01-3dca-metaball-ca`** (3D raymarched metaball / cellular growth). Prompt text is **not** implemented here; only scaffolding for running and comparing it.

## What is intentionally out of scope (so far)

- Automated model calls / API harness  
- Automated screenshot / video capture  
- LLM-as-judge scoring  
- Implementing the demo HTML itself  

## Ready for baseline runs

| Step | Action |
|------|--------|
| 1 | Copy `prompts/01-3dca-metaball-ca/prompt.txt` into the model under test |
| 2 | Write result to `workspace/output.html` |
| 3 | Open in browser; fill scores in a new `runs/<date>_<model>/` folder |
| 4 | Update `results/leaderboard.md` |

## Key paths

| Path | Role |
|------|------|
| `prompt.txt` | Convenience copy of primary prompt |
| `prompts/01-3dca-metaball-ca/` | Canonical task + `task.json` |
| `workspace/` | Active artifact |
| `runs/_template/` | Clone for each finished trial |
| `results/leaderboard.md` | Comparison table |
| `README.md` | Full conventions |

## Reference pattern

[BridgeBench UI Bench](https://www.bridgebench.ai/ui-bench) — 12 tasks, single HTML artifacts, scores on **completeness / visual / interactivity**, side-by-side model comparison (e.g. lava lamp). Community prompts: https://www.bridgebench.ai/test-prompts

## Next agent / human

- Do **not** change the prompt mid-baseline without recording a new `prompt_version` in `meta.json`.  
- Prefer one-shot runs for comparable numbers.  
- Optional future: multi-task prompts under `prompts/02-…`, local static gallery page, or screenshot capture script.
