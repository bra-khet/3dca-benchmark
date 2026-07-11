# Run notes

**Task:** `01-3dca-metaball-ca`  
**Model:** OpenAI GPT-5.6 (`gpt-5-6-sol`)  
**Date:** 2026-07-09  
**Shots:** one  
**Status:** passed (artifact complete; scores pending browser review)

## Scores (0–100, BridgeBench-style)

| Dimension       | Score | Notes |
|-----------------|------:|-------|
| Completeness    |       | Sim + raymarch + UI shipped; score after open |
| Visual          |       | ECOTONE styling, grain, glow, soft shadows, trail memory |
| Interactivity   |       | Orbit, zoom, full Growth Protocol panel, pause/step/reset |
| Composite       |       | |

## Latency / cost

- Generation latency (ms): —
- Cost (USD): —

## First impression

Self-contained single HTML (~67KB, branded **ECOTONE — Cellular Morphogenesis**). WebGL2 raymarched metaball colony with a polished glass control panel. Originally produced under the wrong archive path (`results/`); restructured into `runs/` without editing HTML body content (filename only: `3dca-metaball-ca.html` → `output.html`).

## What worked

- Blob array with neighbor field, birth threshold, growth/attrition, budding, energy transfer
- Smooth-union metaball SDF in fragment shader (`MAX_BLOBS` 96 GPU; default population cap 72)
- Soft shadow + AO, energy-driven emissive tissue color + palette modes
- Post path with trail memory / bloom-style persistence
- Orbit camera (auto drift + drag + wheel), pause / step / reseed, alive + generation + mean energy + FPS
- Vanilla “Growth Protocol” sliders for major rules; keyboard space/P (and step when paused)
- Resize handling, WebGL2 error fallback UI

## What failed or was missing

- None verified yet (HTML not opened for scoring in this archive pass)
- Folder slug keeps `_sol` from the operator’s archive name; treat as GPT-5.6 baseline unless you rename later

## Stability (~1–2 min open)

- Defaults: maxBlobs 72, birth threshold 3, moderate spawn/death/energy share
- Open in browser and watch for extinction vs fill / overcrowding

## Browser / machine

- Browser: (fill after review)
- GPU / machine: (fill after review)
- FPS feel: (fill after review)

## Prompt requirement checklist

| Requirement | Status | Notes |
|-------------|--------|-------|
| Blob sim + neighbor rules | yes | O(n²)-style neighbor field; grow / bud / attrition |
| Raymarched smooth-union metaballs | yes | WebGL2 fullscreen canvas raymarcher |
| Lighting / emissive by energy | yes | key lighting + soft shadow + energy glow |
| Camera orbit + mouse | yes | auto orbit drift + drag + wheel |
| Tunable params UI | yes | Growth Protocol panel (vanilla, not dat.GUI) |
| Pause / reset / alive count | yes | + step + gen + mean energy + FPS |

## Archive note

- Artifact moved into this folder from a misdirected `results/` write path
- **HTML content not modified** — only renamed to match run template (`output.html`)
- Added `meta.json` + `notes.md` to match `runs/2026-07-09_grok-4-5/`

## Verdict

Ready for human open-and-score. Path: `runs/2026-07-09_gpt-5-6-sol/output.html`.
