# Archived runs

Each completed (or abandoned-but-interesting) trial gets its own folder — one model output for one task prompt, same spirit as BridgeBench’s per-model HTML artifacts.

## Create a new run archive

```powershell
$name = "$(Get-Date -Format yyyy-MM-dd)_model-slug"
Copy-Item -Recurse runs\_template "runs\$name"
Copy-Item workspace\output.html "runs\$name\output.html" -Force
# edit runs\$name\meta.json  (scores, model id, latency, status)
# edit runs\$name\notes.md   (optional qualitative notes)
```

Then append a row to `../results/leaderboard.md`.

## Folder name

`YYYY-MM-DD_<model-slug>` — e.g. `2026-07-09_claude-opus-4-8`.

Same model same day: `_r2`, `_temp0`, `_multi`.

## Optional files

| File | Purpose |
|------|---------|
| `output.html` | Required — the one-shot artifact |
| `meta.json` | Required — scores + provenance |
| `notes.md` | Qualitative review |
| `preview.png` | Optional still frame for gallery comparison |
