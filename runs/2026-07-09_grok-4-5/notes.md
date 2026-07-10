# Run notes

**Task:** `01-3dca-metaball-ca`  
**Model:** xAI Grok 4.5  
**Date:** 2026-07-09  
**Shots:** one  
**Status:** passed (artifact complete; scores pending browser review)

## Scores (0–100, BridgeBench-style)

| Dimension       | Score | Notes |
|-----------------|------:|-------|
| Completeness    |       | Sim + raymarch + UI shipped; score after open |
| Visual          |       | Organic palette, glow, soft shadows, vignette |
| Interactivity   |       | Orbit, zoom, sliders, pause/step/reset, HUD |
| Composite       |       | |

## Latency / cost

- Generation latency (ms): —
- Cost (USD): —

## First impression

Self-contained single HTML (~28KB). WebGL2 fullscreen triangle raymarcher; JS cellular sim separate from shader. Defaults tuned for ~48 seed blobs, max 64 (hard GPU cap 80).

## What worked

- Blob array with pos / radius / energy / age + neighbor rules (grow, spawn, die, energy share)
- Polynomial smoothMin metaball union in fragment shader
- Key + fill + rim lighting, soft shadow, cheap AO, energy-driven emissive + palette
- Smooth sim interpolation, auto-orbit + mouse orbit/zoom
- Vanilla sliders for all major rule params; pause / step / reset; alive + gen + FPS
- Resize handling, vignette + glow post touches
- Top-of-file comment documents rules and tunables

## What failed or was missing

- No dat.GUI (vanilla panel instead — allowed by prompt)
- No true multi-pass bloom (single-pass glow / trail strength instead)
- True frame-history trails approximated via volumetric glow + trail uniform (not a separate history buffer)
- Scores / FPS not yet measured on target hardware

## Stability (~1–2 min open)

- Defaults aim for steady clusters (homeostasis mid-density, soft origin pull, death floor + reseed if empty)
- Open in browser and watch for extinction vs fill

## Browser / machine

- Browser: (fill after review)
- GPU / machine: (fill after review)
- FPS feel: (fill after review)

## Prompt requirement checklist

| Requirement | Status | Notes |
|-------------|--------|-------|
| Blob sim + neighbor rules | yes | O(n²), tunable radius/thresholds |
| Raymarched smooth-union metaballs | yes | IQ polynomial smin |
| Lighting / emissive by energy | yes | key/fill/rim + energy emissive |
| Camera orbit + mouse | yes | auto + drag + wheel |
| Tunable params UI | yes | vanilla sliders |
| Pause / reset / alive count | yes | + step + gen + FPS |

## Verdict

Ready for human open-and-score. Path: `runs/2026-07-09_grok-4-5/output.html` (same as `workspace/output.html`).
