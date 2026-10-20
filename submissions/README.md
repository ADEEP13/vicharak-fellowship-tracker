# Submissions — how to submit

1. Copy `TEMPLATE.json` to a new file named: `<Your-Full-Name-With-Underscores>_<Type>_<YYYY-MM-DD>.json`
   - Name must match `fellows.csv` (case-insensitive), e.g. `Arjun_A`.
   - Type must be one of: PurchaseProof, Blog, Linkedin, X, Project, Workshop, Documentation contribution, Video, YT Video, Reel, Fellowship Referral, Bug.
   - **First PR must be PurchaseProof**: your dev-kit proof (board photo / invoice image link). Title it `[PurchaseProof] Your Name`. Until accepted, Kit shows NO in the score block.
2. Fill all fields. Link must start with http:// or https://.
   - `github`: your GitHub username/URL (the account opening the PR). It must map to your `fellow` name via `fellows.csv` or `github_overrides.json` — points always go to the `fellow` name, never to the raw account. A mismatch fails CI.
3. Open a Pull Request. PR title format (important):
   `[PurchaseProof]` (first PR only) `[Blog]` `[Linkedin]` `[X]` `[Project]` `[Workshop]` `[Documentation contribution]` `[Video]` `[YT Video]` `[Reel]` `[Fellowship Referral]` `[Bug]`
4. One submission = one JSON file = one PR (easier to accept/reject). Do not bundle multiple links in one file.
5. If maintainer merges, points auto-allocate. If closed, no points.

## Rules that fail CI (read before pushing)

- **Your PR must add EXACTLY ONE new file** under `submissions/`. The `file-guard` check enforces this.
- **The filename MUST end in `.json`.** The scorer only reads `submissions/*.json`. A file named
  `..._2026_10_15` (no extension) is silently ignored and you get **0 points with no error**.
- **Do NOT run the scorer locally** (`python scripts/update_scores.py`). It rewrites `README.md`,
  `SCORES.md`, `allocations/`, `fellowship_scores.pdf` and `submissions/INDEX.*`. If you commit
  those, your PR conflicts with `main` and CI fails. They are bot-owned — the bot regenerates
  them automatically after merge.
- **Do NOT edit or delete an existing submission.** Merged submissions are permanent records.
- Never touch `points.json`, `fellows.csv`, `scripts/`, `.github/`, `SCORES.md`, `README.md`
  or `allocations/`.

If your PR shows a conflict or a `file-guard` failure, see [`docs/FORKS.md`](../docs/FORKS.md).

## Before you submit a Project

Check [`docs/PROJECTS.md`](../docs/PROJECTS.md) first — it lists every project already
accepted in this program and the 32 upstream examples in `vicharak-in/shrike`. If your
idea is already listed, build something different or extend it meaningfully.

## Single-name listing (auto-generated)
- [`INDEX.md`](INDEX.md) — all accepted submissions grouped under a single fellow name (`## Name - N submission(s), P pts` + bullet per link). Start here to browse.
- [`INDEX.json`](INDEX.json) — same data, machine-readable (`{ "Fellow Name": [{type, points, title, link, date, file}] }`).
- Both regenerate on every merge. Do not hand-edit (overwritten). Ignored as input by the scorer.

Example file: `Arjun_A_Blog_2026-09-28.json`
```json
{
  "fellow": "Arjun A",
  "type": "Blog",
  "title": "My Axon Lite build log",
  "link": "https://medium.com/@arjun/my-axon-build",
  "date": "2026-09-28"
}
```
