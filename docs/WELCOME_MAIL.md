# Welcome mail for new fellows

Subject: Welcome to the Vicharak Campus Fellowship — join the groups + submit your kit proof

Hi,

Welcome aboard! You're registered in the fellowship tracker. Here's how to get started.

**1. Join the groups**
- WhatsApp: https://chat.whatsapp.com/JcvTgHxRw4GAltU0QsdNfg?mode=gi_t
- Discord: https://discord.gg/CafTF5Wwx

**2. Your first task (mandatory): kit purchase proof**
Nothing else counts until this is accepted. Steps (full guide: `docs/JOIN.md` in the repo):
1. Photograph your board/invoice, upload it somewhere public (Google Drive / Imgur / LinkedIn post, "anyone can view"), copy the `https://...` link.
2. On GitHub (https://github.com/nilangwork17/vicharak-fellowship-tracker), copy `submissions/TEMPLATE.json` to `submissions/<Your-Name>_PurchaseProof_<YYYY-MM-DD>.json` (e.g. `submissions/Arjun_A_PurchaseProof_2026-09-28.json`). Use your **exact name as registered** and paste the photo link in the `link` field.
3. Open a PR titled `[PurchaseProof] Your Name` and paste the same link in the description.
4. Once merged, your `Kit` flips to `YES` on the scoreboard — you're unlocked.

**3. Then submit your work for points (need 250 to become ELIGIBLE)**
Points: Blog 40, LinkedIn 40, X 40, Project 70, Workshop 100, Documentation contribution 30, YT longform Video 90, YT shorts 50, Insta reel 50, Fellowship Referral 20, Bug 25. PostedLink: 0 (auto-approved, awards points of the original type on platform verification). PurchaseProof = 0 points, but it unlocks you.

**Two-stage flow for social media (Blog, LinkedIn, X, YT longform Video, YT shorts, Insta reel):**
1. **Draft stage**: submit `type: "Blog"` (or other social type) with `link` = your Google Doc draft. I review content, merge → 0 points. Bot comments: "Content approved! Now post on the platform and submit the final link for your points."
2. **Posted link stage**: after posting, open a new PR with `type: "PostedLink"`, `for_type: "Blog"` (or your type), and `link` = the published URL. The bot auto-verifies the platform and auto-merges → points given. No manual approval needed.

**Other types (Project, Workshop, Documentation contribution, Bug, Fellowship Referral, PurchaseProof):** one PR, admin reviews and merges, points given. No posted link step.

1. Prepare your work as a **draft first** (Google Doc, public link) — do NOT post publicly yet.
2. One submission = one JSON file = one PR, titled `[Type] Your Name` (e.g. `[Blog] Arjun A`).
3. After your PR is merged, post the final version on the actual platform (Medium / x.com / LinkedIn / GitHub / YouTube).
4. Track your score on the live leaderboard in the repo README (`SCORES.md` has the full table).

**Please note:** PRs other than purchase proof will be closed until your Kit shows YES. One file per PR, and double-check your `fellow` name spelling — mismatches fail automatically.

Good luck, and see you in the groups!

— Team Vicharak
