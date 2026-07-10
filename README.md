# 3DCA Benchmark

Benchmark workspace for one-shot generation of a **self-contained HTML** raymarched metaball / cellular-growth demo (see `prompt.txt`).

Use this folder to:

- Keep a single **canonical prompt** (`prompt.txt`)
- Work on the current attempt in **`workspace/`**
- Archive past model runs under **`runs/`**
- Track comparisons in **`results/`**

This is intentionally light scaffolding — not an automated harness.

## Quick start

1. Copy `prompt.txt` into your model/tool of choice (do not edit the prompt for a fair baseline; if you do, note it in `meta.json`).
2. Save the model’s one-shot HTML to `workspace/output.html` while iterating.
3. When a run is “done” (accepted, abandoned, or scored), archive it:

   ```text
   runs/<YYYY-MM-DD>_<model-slug>/
     meta.json
     output.html
     notes.md          (optional)
   ```

4. Add a row to `results/leaderboard.md`.

## Directory layout

```text
3dca-benchmark/
├── prompt.txt              # canonical benchmark prompt (source of truth)
├── README.md               # this file
├── workspace/              # active scratch — current trial only
│   └── output.html         # working one-shot artifact (optional until first run)
├── runs/
│   ├── _template/          # copy this for each new archived run
│   │   ├── meta.json
│   │   ├── notes.md
│   │   └── output.html     # placeholder
│   └── <date>_<model>/     # one folder per completed trial
└── results/
    └── leaderboard.md      # summary table of past runs
```

## Run naming

Prefer:

```text
runs/2026-07-09_claude-opus-4/
runs/2026-07-09_gpt-4o/
runs/2026-07-10_grok-4/
```

Slug rules: lowercase, hyphens, no spaces. Date = day the HTML was produced (local).

## Scoring (informal)

There is no automatic scorer. Suggested dimensions for `meta.json` / leaderboard:

| Field            | Meaning                                              |
|------------------|------------------------------------------------------|
| `opens`          | Loads with no console errors                         |
| `sim_alive`      | Simulation does not go extinct / fill instantly      |
| `raymarch_ok`    | Visible metaballs / SDF scene                        |
| `controls_ok`    | Sliders / orbit / pause roughly work                 |
| `visual`         | 1–5 subjective visual quality                        |
| `code_quality`   | 1–5 structure / comments / maintainability           |
| `fps_feel`       | 1–5 perceived performance on your machine            |
| `notes`          | Free-form issues (artifacts, missing features, etc.) |

## Fair comparison tips

- Always start from the **same** `prompt.txt` for a baseline.
- One shot preferred; if you allow multi-turn fixes, set `"shots": "multi"` and note turns in `meta.json`.
- Record model id, temperature, and date.
- Do not commit huge binary dumps; HTML only.

## Related idea

Same spirit as creative one-shot “lava lamp” style visual demos: fixed prompt, many models, archive each HTML + short notes, compare by eye and checklist.
