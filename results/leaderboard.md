# Leaderboard

Informal comparison of archived runs (BridgeBench-style dimensions). Fill after each trial lands in `runs/`.

## `01-3dca-metaball-ca`

| Date | Model | Shots | Status | Completeness | Visual | Interactivity | Composite | Latency | Cost | Path | Summary |
|------|-------|-------|--------|-------------:|-------:|--------------:|----------:|--------:|-----:|------|---------|
| 2026-07-09 | grok-4-5 | one | passed | — | — | — | — | — | — | [`../runs/2026-07-09_grok-4-5/output.html`](../runs/2026-07-09_grok-4-5/output.html) | WebGL2 raymarched metaball CA; full UI; scores pending browser review |
| 2026-07-09 | gpt-5-6-sol | one | passed | — | — | — | — | — | — | [`../runs/2026-07-09_gpt-5-6-sol/output.html`](../runs/2026-07-09_gpt-5-6-sol/output.html) | ECOTONE WebGL2 metaball CA; polished panel + trail post; scores pending browser review |

## `02-simple-distillation-sim`

| Date | Model | Shots | Status | Completeness | Visual | Interactivity | Composite | Latency | Cost | Path | Summary |
|------|-------|-------|--------|-------------:|-------:|--------------:|----------:|--------:|-----:|------|---------|
| 2026-07-10 | grok-4-5 | one | passed | — | — | — | — | — | — | [`../runs/2026-07-10_grok-4-5/output.html`](../runs/2026-07-10_grok-4-5/output.html) | Canvas 2D distillation particles; reference glassware; scores pending browser review |

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
