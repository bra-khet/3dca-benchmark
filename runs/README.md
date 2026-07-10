# Archived runs

Each completed (or abandoned-but-interesting) trial gets its own folder.

## Create a new run archive

1. Copy the template:

   ```powershell
   $name = "$(Get-Date -Format yyyy-MM-dd)_model-slug"
   Copy-Item -Recurse runs\_template "runs\$name"
   ```

2. Replace `runs\<name>\output.html` with the model artifact (from `workspace/` or the chat export).

3. Edit `meta.json` (model id, date, scores, checklist).

4. Fill `notes.md` if useful.

5. Add a row to `../results/leaderboard.md`.

## Folder name

`YYYY-MM-DD_<model-slug>` — e.g. `2026-07-09_claude-sonnet-4`.

If you re-run the same model the same day, append a short suffix: `_r2`, `_temp0`, `_multi`.
