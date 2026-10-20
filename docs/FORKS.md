# Fork behaviour & why your PR may conflict

## TL;DR for students

- **Do NOT run the scorer locally** (`python scripts/update_scores.py`). It rewrites
  `README.md`, `SCORES.md`, `allocations/`, `fellowship_scores.pdf` and `submissions/INDEX.*`.
  If you commit those, your PR will conflict with `main` and CI will fail.
- **Your PR must add exactly ONE new file** under `submissions/`, named
  `submissions/<Your-Name>_<Type>_<YYYY-MM-DD>.json`.
- **The file MUST end in `.json`.** The scorer only reads `submissions/*.json`. A file
  called `..._2026_10_15` (no extension) is silently ignored and you score 0 points
  with no error.
- **Never edit or delete an existing submission.** A merged submission is a permanent
  record. If you need to correct it, ask the admin.
- Everything else (`README.md`, `SCORES.md`, `points.json`, `fellows.csv`, `scripts/`,
  `.github/`, `allocations/`) is admin/bot-owned. Touching it fails CI.

## What to do if you get it wrong

You will see one of these on your PR:

### "file-guard failed"

The CI check `file-guard` enforces the rules above. Click the failing check to see
exactly which file is the problem. Common causes:

| Message | What to do |
|---|---|
| `must add exactly ONE new submissions/*.json file (found N)` | You committed extra files. Revert everything except your one submission file. |
| `these files have no .json extension` | Rename your file to end in `.json`, e.g. `X_Project_2026-10-15.json`. |
| `not allowed: modified: README.md` | You ran the scorer locally. Revert those files. |

### "This branch has conflicts that must be resolved"

Someone merged to `main` after you branched, and the files you committed overlap.
The fix is the same: your branch should contain only your one submission file.

Ask the admin to reset your branch, or do it yourself:

```bash
# keep ONLY your submission file, drop the generated ones
git checkout main -- README.md SCORES.md allocations/ fellowship_scores.pdf submissions/INDEX.json submissions/INDEX.md
git add -A
git commit -m "Keep only my submission file"
git push --force
```

If your branch also *modified* an existing submission file, restore it too:

```bash
git checkout main -- submissions/<Existing-File>.json
```

## Why this happens (for the curious)

Your PR comes from a **fork** of this repo. Forks inherit the GitHub Actions workflows,
so before this was fixed, pushing to *your fork's* `main` branch also ran the scoring
bot inside your fork. The bot regenerated the score files and committed them into your
branch, so every PR carried 6-8 extra generated files and collided with `main`.

The bot now skips forks (`if: github.event.repository.fork == false`), so this class of
problem is gone for new forks. Older forks may still show it - the admin can reset the
branch for you.

## Quick checklist before you open the PR

1. One new file only: `submissions/<Your-Name>_<Type>_<YYYY-MM-DD>.json`
2. Filename ends in `.json`
3. `fellow` matches your name in `fellows.csv` exactly
4. `type` is one of the allowed types
5. `link` starts with `https://` and opens without login
6. `date` is `YYYY-MM-DD`
7. `github` is your GitHub username/URL
8. PR title is `[Type] Your Name`
9. `git status` shows only your new file
