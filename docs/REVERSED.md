# Reversed submissions

*Maintained by the admin. Last updated 2026-10-20.*

When a merged PR needs to be taken back, GitHub does **not** allow a merged PR to be
un-merged — the purple `Merged` badge is permanent (the API rejects reopening,
re-closing, and un-setting `merged_at`). The standard way to reverse a merge is a
**revert commit**, which undoes the content and the points but leaves the original
PR marked as merged.

So every reversal is recorded in two places:

1. **This file** — the authoritative list.
2. **A `reverted` label** on the original PR, plus a comment explaining the reversal.

## Reversed

| PR | Fellow | Submission | Points impact | Reversal PR | Notes |
|---|---|---|---|---|---|
| #63 | Nathan Mathews | Project — "Tiny ILA for Shrike" (`Nathan_Mathews_Project_2026-10-17.json`) | 70 → deducted. Total 110 → 40 | #74 | Blog (40) and PurchaseProof (Kit=YES) kept. Project was rejected; can be re-submitted as a fresh PR. |
| #74 | — | (revert PR) | — | — | Merged, then superseded by this record. |

## Why the original PR still shows "Merged"

Rewriting `main` to delete a merge commit was tested and rejected:

- The `Merged` badge does **not** flip to `Closed` even when the merge commit is
  force-pushed out of `main` (verified on a throwaway repo).
- Rewriting history would orphan the merge commits of **8 other PRs** (#66–#74), risking
  them flipping to `Closed` as well — far more damage than the badge is worth.

Reversing via a revert commit is safer: content is removed, points are recalculated by the
bot, and the audit trail stays intact.

## If a reversed submission should be re-reviewed

The fellow opens a **new** PR with only their one file:
`submissions/<Name>_<Type>_<YYYY-MM-DD>.json`. It is scored normally.
