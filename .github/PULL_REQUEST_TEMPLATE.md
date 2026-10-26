## Submission PR — required format

**Title must start with one of:** `[PurchaseProof]` `[Blog]` `[Linkedin]` `[X]` `[Project]` `[Workshop]` `[Documentation contribution]` `[YT longform Video]` `[YT shorts]` `[Insta reel]` `[Fellowship Referral]` `[Bug]` `[PostedLink]`
Example: `[Blog] Arjun A — My Axon Lite build https://medium.com/...`
First PR from any fellow must be `[PurchaseProof] Your Name — board/invoice image link` (0 pts, flips Kit to YES in the score block).
PostedLink PRs are processed automatically if the platform matches and a prior draft exists.

**Checklist (maintainer merges = accept = points):**
- [ ] Added ONE file: `submissions/<Name>_<Type>_<YYYY-MM-DD>.json` (copied from TEMPLATE.json)
- [ ] Filename ends in `.json` (a file without it is invisible to the scorer → 0 points, no error)
- [ ] This PR touches NOTHING else — no `README.md`, `SCORES.md`, `allocations/`, `INDEX.*`, PDF.
      Do not run `python scripts/update_scores.py` locally; the bot regenerates those after merge.
- [ ] Did not edit or delete an already-merged submission
- [ ] `fellow` exactly matches a name in `fellows.csv`
- [ ] `github` is your GitHub username/URL and maps to that fellow (see `github_map.json`; admin fixes via `github_overrides.json`)
- [ ] `type` matches PR prefix
- [ ] `link` starts with http(s):// and is public/openable
- [ ] `date` is YYYY-MM-DD
- [ ] For `PostedLink` type: `for_type` is set to the original social type (Blog, Linkedin, X, YT longform Video, YT shorts, Insta reel)

> Seeing a conflict or a red `file-guard` check? Read [`docs/FORKS.md`](../docs/FORKS.md).
>
> Submitting a **Project**? Check [`docs/PROJECTS.md`](../docs/PROJECTS.md) first — it lists
> every project already accepted plus the upstream examples, so you don't duplicate one.

**Link:**
Paste your Blog / LinkedIn / X / Project repo / Workshop link here:

**Notes for reviewer:**
