# Leaderboard — `01-3dca-metaball-ca`

Informal comparison of archived runs (BridgeBench-style dimensions). Fill after each trial lands in `runs/`.

| Date | Model | Shots | Status | Completeness | Visual | Interactivity | Composite | Latency | Cost | Path | Summary |
|------|-------|-------|--------|-------------:|-------:|--------------:|----------:|--------:|-----:|------|---------|
| — | — | — | — | — | — | — | — | — | — | — | No runs yet |

## How to add a row

1. Archive under `runs/<YYYY-MM-DD>_<model-slug>/`.
2. Score in that run’s `meta.json` / `notes.md`.
3. Append a row here.

## Conventions

- **Status:** `passed` / `partial` / `failed` / `empty`
- **Completeness / Visual / Interactivity / Composite:** 0–100 (integers fine)
- **Latency:** generation time in ms if known, else `—`
- **Cost:** USD if known, else `—`
- **Path:** relative, e.g. [`../runs/2026-07-09_example/output.html`](../runs/_template/output.html)

## Side-by-side review

Open two or more `runs/*/output.html` files in browser tabs (or a simple local static server). Optional: drop a `preview.png` screenshot into each run folder later for gallery-style comparison, similar to BridgeBench’s artifact thumbnails.
