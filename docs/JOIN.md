# Joining the repo (purchase proof = first PR)

Public to view. To submit, your **first PR must be your purchase proof**.

## Student — 3 simple steps
1. Submit your screenshot in your submission file: copy `submissions/TEMPLATE.json` → `submissions/<Your-Name>_PurchaseProof_<YYYY-MM-DD>.json` (example: `submissions/Arjun_A_PurchaseProof_2026-09-28.json`). Upload your board / invoice photo somewhere (Google Drive / Imgur / Linkedin post, etc. with public view on) and paste that `https://...` link in the `link` field.
2. Open a PR with that link, titled `[PurchaseProof] Your Name`.
3. I check it. If it is valid purchase proof, I accept (merge) the PR and your Kit status in the live score list flips to `YES`.

## After proof is accepted
Only after your PurchaseProof PR is merged will regular submissions be accepted:
- Blog / Linkedin / X / Project / Workshop / Documentation contribution / YT longform Video / YT shorts / Insta reel / Fellowship Referral / Bug / PostedLink
- One submission = one JSON file = one PR, e.g. `submissions/Arjun_A_Blog_2026-09-28.json` with PR title `[Blog] Arjun A — https://...`

### Two-stage flow for social media types (Blog, Linkedin, X, YT longform Video, YT shorts, Insta reel)

Social media submissions follow a two-stage process to ensure students actually post on the platform:

**Stage 1 — Draft (admin reviews, 0 points):**
1. Submit `type: "Blog"` (or other social type) with `link` = your Google Doc draft.
2. Admin reviews content, merges → 0 points (content approved, pending post).
3. Bot comments: "Content approved! Now post on the platform, then submit the final link."

**Stage 2 — Posted link (system verifies, points given):**
1. Post the final version on the platform.
2. Open a new PR with `type: "PostedLink"`, `for_type: "Blog"` (or your type), and `link` = the published URL.
3. System verifies: platform matches + prior draft approved (title similarity ≥ 75%) → points given.
4. If verification fails → PR stays open for admin review.

**Other types (Project, Workshop, Documentation contribution, Bug, Fellowship Referral, PurchaseProof):** one PR, admin reviews and merges, points given. No posted link step.

> If your first PR is not the purchase proof, it will be closed / not accepted. Submit the PurchaseProof PR first, then resubmit the others.

## Admin
I check the PR. If it is valid purchase proof, I merge it and the Kit status flips to `YES` automatically.
