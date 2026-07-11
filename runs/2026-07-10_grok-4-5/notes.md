# Run notes

**Task:** `02-simple-distillation-sim`  
**Model:** xAI Grok 4.5  
**Date:** 2026-07-10  
**Shots:** one  
**Status:** passed (artifact complete; scores pending browser review)

## Scores (0–100, BridgeBench-style)

| Dimension       | Score | Notes |
|-----------------|------:|-------|
| Completeness    |       | All core zones + UI shipped; score after open |
| Visual          |       | Reference-like black/cyan apparatus; polish TBD |
| Interactivity   |       | Heat/cool/speed/N, ±20, pause/reset, live HUD |
| Composite       |       | |

## Latency / cost

- Generation latency (ms): —
- Cost (USD): —

## First impression

Self-contained single HTML (~canvas 2D, no external deps). Dark lab aesthetic matching `references/img/simple-distillation.png`: blue hot plate (11/12), yellow bath (15), cyan Liebig condenser with inlet/outlet arrows, hanging red thermometer, receiver over cyan cool bath (16).

## What worked

- Particle model: pos / vel / temp / state (`liquid` | `vapor`), max 500
- Zone heating in flask bottom ∝ Heat Power; probabilistic vaporization + upward kick
- Condenser jacket cooling ∝ Cooling Rate; condensation → slope-guided drip
- Receiver pool accumulation + fill bar + distilled counter
- Region + soft circle/tube containment (minimize escapes)
- UI: heat, cool, sim speed, particle count slider, +20/−20, pause, reset
- Visuals: temp-colored particles, bubbles, jacket flow marks, thermometer tracks flask avg T
- Top-of-file comment block documents toy thermodynamics

## What failed or was missing

- No true multi-component mixture / boiling-point separation (prompt is water-only toy)
- Line-segment collisions are simplified (region clamps + condenser radial walls)
- Glassware is schematic (matches reference style) not photoreal
- Scores / FPS not yet measured on target hardware

## Stability (~1–2 min open)

- Defaults: heat 55, cool 70, N=280, speed 1× — should show continuous boil → vapor path → condensate → receiver fill
- Open in browser; if vapor stalls, raise heat; if no condensation, raise cooling

## Browser / machine

- Browser: (fill after review)
- GPU / machine: (fill after review)
- FPS feel: (fill after review)

## Prompt requirement checklist

| Requirement | Status | Notes |
|-------------|--------|-------|
| Single HTML, canvas + rAF | yes | embedded CSS/JS, no CDN |
| 300–500 particles max | yes | slider 50–500, default 280 |
| Liquid/vapor + temp | yes | phase change rules |
| Boiling flask heat zone | yes | bottom heat + bubbles |
| Condenser cool + condense | yes | jacket zone + drip along slope |
| Receiver accumulation | yes | pool + bar + counter |
| Wall / boundary containment | yes | flask/tube/recv clamps |
| Heat / cool / N / speed / pause / reset | yes | side panel |
| Thermometer, legend, explanation | yes | |
| Reference layout match | yes | black bg, cyan jacket, numbered bath/plate |

## Verdict

Ready for human open-and-score. Path: `runs/2026-07-10_grok-4-5/output.html` (same as `workspace/output.html`).
