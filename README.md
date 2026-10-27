# Vicharak Campus Fellowship - Submission Tracker

Think of this repo as your fellowship marksheet.

You do work outside (blog, video, LinkedIn post, project), you send us the link here, I press Accept, and a robot automatically gives you points and updates the score list below.

You need 250 points to become ELIGIBLE.

Points list (from `points.json`):
Blog = 40, Linkedin = 40, X = 40, Project (GitHub) = 70, Workshop = 100, Documentation contribution = 30, YT longform Video = 90, YT shorts = 50, Insta reel = 50, Fellowship Referral = 20, Bug = 25, PostedLink = 0 (verified, awards points[for_type] on platform verification). PurchaseProof = 0 points, but it unlocks you.

Student list comes from `fellows.csv` (69 fellows).

## Step 0 - Join first: purchase proof must be your first PR

You cannot submit anything until I know you have the kit. So your very first submission must be your kit proof.

1. Upload your kit photo somewhere public. Take a photo of your board / invoice, upload it to Google Drive / Imgur / LinkedIn post (set to Anyone can view), and copy that `https://...` link.
2. Fill the form: copy `submissions/TEMPLATE.json` to a new file named `submissions/<Your-Name>_PurchaseProof_<YYYY-MM-DD>.json`. Example: `submissions/Arjun_A_PurchaseProof_2026-09-28.json`. Paste your photo link in the `link` field.
3. Send it for checking: open a PR titled `[PurchaseProof] Your Name`, and paste the same link in the PR description too.
4. I check it. I open your link and see if it is really your board / bill. If yes, I press Merge (Accept) and your Kit in the score list below changes to `YES`. If no, I close it and you fix and resend.

Rule: If your first PR is not the purchase proof, I will close it. Do proof first, then do the rest.

Full steps with pictures in words: [`docs/JOIN.md`](docs/JOIN.md).

## Step 1 - How to send your regular work (after proof is accepted)

Only after your PurchaseProof is accepted, do this for Blog, Linkedin, X, Project, etc.

1. Make your draft viewable first - do NOT post on social media yet. Put your draft in a Google Doc (or similar) with `Anyone with link can view`, and copy that `https://...` link. This is what you send for review. Only after I approve the PR, post it on the dedicated platform - Medium for Blog, x.com for X, LinkedIn for Linkedin, GitHub for Project, YouTube for YT longform Video / YT shorts, Instagram for Insta reel.
2. Fill the form: copy `submissions/TEMPLATE.json` to `submissions/<Your-Name>_<Type>_<YYYY-MM-DD>.json`. Example: `submissions/Arjun_A_Blog_2026-09-28.json`.
   - `fellow`: your exact name from `fellows.csv`, example `Arjun A`
   - `type`: one of - Blog, Linkedin, X, Project, Workshop, Documentation contribution, YT longform Video, YT shorts, Insta reel, Fellowship Referral, Bug
   - `title`: short name of your work
   - `link`: paste your Google Doc draft link here for review (must start with `https://` and open without login). After approval you will post the final link on the dedicated platform.
   - `date`: today in `YYYY-MM-DD`
3. Send it: open a PR titled `[Type] Your Name`. Example: `[Blog] Arjun A`. Paste the same Google Doc link in the PR description so I can click fast.
4. One file = one PR. Do not put 5 links in one file. Send 5 PRs.

### Two-stage flow for social media submissions (Blog, Linkedin, X, YT longform Video, YT shorts, Insta reel)

Social media types follow a two-stage process to ensure students actually post on the platform:

**Stage 1 — Draft (admin reviews, 0 points):**
1. Submit `type: "Blog"` (or other social type) with `link` = your Google Doc draft. Title it `[Blog] Your Name`.
2. I review the content by eye. If good, I merge → "content approved" (0 points allocated).
3. Bot posts an auto-comment: "Content approved! Now post on Medium and submit the final link for your points."

**Stage 2 — Posted link (system verifies, points given):**
1. Post the final version on the platform (Medium, x.com, LinkedIn, YouTube, Instagram).
2. Open a **new PR** with `type: "PostedLink"`, `for_type: "Blog"` (or your type), and `link` = the published URL. Title it `[PostedLink] Your Name`.
3. The system verifies: is the URL from the right platform? Was a draft already approved (title match ≥ 75%)?
   - If yes → **system processes it** → points allocated (Blog = 40, etc.).
   - If no → system comments the specific issue → PR stays open for me to review.
4. No manual approval needed. Points appear automatically.

**Note:** If you skip the draft stage and submit `PostedLink` directly, the bot will leave it for admin review (no auto-approval) since no prior draft was found.

### Other submission types (Project, Workshop, Documentation contribution, Bug, Fellowship Referral, PurchaseProof)

These work as before: one PR, admin reviews and merges, points given. No posted link step needed.

## Step 2 - How I check and give points

I am the checker, the robot is the calculator.

1. You tell me what it is: your `type` + PR title says `[Blog]` or `[X]`, etc.
2. Robot checks only format: is the name correct? Does link start with `https://`? Is type valid?
3. I click and verify by eye: I open your Google Doc draft, check it matches the claimed `type` (`[Blog]` = blog draft, `[X]` = X post text, etc). If good, I press Merge = Accept. You then post the final version on the dedicated social platform. If not good, I press Close = Reject and you get 0, fix and resend.
4. After Merge, the robot runs automatically (`.github/workflows/score.yml` + `scripts/update_scores.py`):
   - collects all accepted links
   - groups them by person and type
   - rewrites your marksheet files and updates the live score list below

So: your title is your claim, my Merge is the approval.

## Step 3 - Where to see your points

- Live table below in this README (top 20, auto-updated on every Merge, do not edit it)
- Full table: [`SCORES.md`](SCORES.md)
- Computer file: [`allocations/summary.csv`](allocations/summary.csv)
- PDF marksheet: [`fellowship_scores.pdf`](fellowship_scores.pdf)
- Per-person file: `allocations/<Your-Name>.csv` looks like this:

```
,Submission 1,Submission 2,Submission 3,Submission 4,Submission 5,Points
Names,Your Name,,,,,
Github,<link>,<link>,,,, <pts>
Linkedin,<link>,...,,, <pts>
Blog,...
X,...
Workshop,...
Total,,,,,,<total>
```

Points = number of accepted links x points for that type. Total = sum of all. 250+ = ELIGIBLE, below = BELOW. Social media types (Blog, Linkedin, X, YT longform Video, YT shorts, Insta reel) follow a two-stage flow: draft (0 points) → PostedLink (full points, verified). Other types are treated normally.

## What is inside this repo (simple map)

- `fellows.csv` - class list. Do not edit by hand.
- `points.json` - points rule book. If I change points here, robot follows it.
- `submissions/` - your filled forms only (JSON files). This is the only folder you touch.
- `allocations/` - auto-made marksheets. Do not edit, robot overwrites them.
- `scripts/update_scores.py` - robot brain. Run `python scripts/update_scores.py` to test locally.
- `fellowship_scores.pdf` - auto-made PDF of all scores.
- `.github/workflows/score.yml` - scoring bot (runs on merge, regenerates allocations/scores).
- `.github/workflows/auto-approve-posted-link.yml` - auto-verifies posted link PRs for social media types.
- `docs/JOIN.md` - how to join (purchase proof = first PR).
- `docs/FORKS.md` - why your PR may conflict, and how to fix it.
- `docs/PROJECTS.md` - already-accepted projects + upstream examples. **Check this before submitting a Project.**
- `docs/REVERSED.md` - submissions whose merge was reversed (points deducted).

## For Admin (me)

- Repo: https://github.com/nilangwork17/vicharak-fellowship-tracker
- Keep `main` protected - only via PR, no direct push.
- To update students: re-export `Fellowship program.xlsx` to `fellows.csv`.

## Live Score List (auto-updated on every merge, do not edit below)
<!-- SCORES_START -->
_Updated 2026-10-27 06:51 UTC - Threshold 250 - 13/69 with points_

| Rank | Fellow | GitHub | Kit | Total | Status |
|---:|---|---|---|---:|---|
| 1 | [yatharth vishwa](allocations/yatharth_vishwa.md) | @yatharthvishwa | YES | **220** | BELOW |
| 2 | [Amaan Pathan](allocations/Amaan_Pathan.md) | @amaan9737 | YES | **150** | BELOW |
| 3 | [Saksham Sud](allocations/Saksham_Sud.md) | @geneticscrol | YES | **140** | BELOW |
| 4 | [Nathan Mathews](allocations/Nathan_Mathews.md) | @deagle2 | YES | **110** | BELOW |
| 5 | [Ankit raj](allocations/Ankit_raj.md) | @ankitra-j | YES | **80** | BELOW |
| 6 | [Harshit Kumar Sharma](allocations/Harshit_Kumar_Sharma.md) | @harshit2387 | YES | **80** | BELOW |
| 7 | [Rujul Rajeev Rumale](allocations/Rujul_Rajeev_Rumale.md) | @rujul-rumale | YES | **80** | BELOW |
| 8 | [Adeep AG](allocations/Adeep_AG.md) | @adeep13 | YES | **70** | BELOW |
| 9 | [ANNESTIO PIETY CASTANHA](allocations/ANNESTIO_PIETY_CASTANHA.md) | @apcetc | YES | **70** | BELOW |
| 10 | [Revand Pradeep](allocations/Revand_Pradeep.md) | @revx5 | YES | **70** | BELOW |
| 11 | [Shreya Veni](allocations/Shreya_Veni.md) | @concatenate-this | YES | **40** | BELOW |
| 12 | [Vaibhav Santosh Tiwari](allocations/Vaibhav_Santosh_Tiwari.md) | @orignalbox | YES | **40** | BELOW |
| 13 | [Veer Kishan Whabi](allocations/Veer_Kishan_Whabi.md) | @veeru24ec006 | YES | **40** | BELOW |
| 14 | [Aaditya Goswami](allocations/Aaditya_Goswami.md) | @aadii02 | NO | **0** | BELOW |
| 15 | [Abhishek Jain](allocations/Abhishek_Jain.md) | @abhishek261007 | NO | **0** | BELOW |
| 16 | [Aditya Nukala](allocations/Aditya_Nukala.md) | @adikp98 | YES | **0** | BELOW |
| 17 | [Aditya Reddy](allocations/Aditya_Reddy.md) | @aditya-1020 | NO | **0** | BELOW |
| 18 | [Aman Sharma](allocations/Aman_Sharma.md) | @captain1508 | NO | **0** | BELOW |
| 19 | [Amrutha M](allocations/Amrutha_M.md) | @amrutham-24 | NO | **0** | BELOW |
| 20 | [Anandu Rajan](allocations/Anandu_Rajan.md) | @anandurajan1209 | NO | **0** | BELOW |

_Showing top 20 of 69 - full list in [SCORES.md](SCORES.md)_
<!-- SCORES_END -->

Full table: [`SCORES.md`](SCORES.md) · Machine-readable: [`allocations/summary.csv`](allocations/summary.csv) · PDF: [`fellowship_scores.pdf`](fellowship_scores.pdf)

## Projects (auto-updated on every merge, do not edit below)
<!-- PROJECTS_START -->
_Updated 2026-10-27 06:51 UTC — 9 approved, 0 in review_

### Approved Projects
| Fellow | Project | Link |
|---|---|---|
| Adeep AG | Geto Web IDE : For Shrike Series board(RP2040 & RP2350) | https://github.com/ADEEP13/IDE |
| Amaan Pathan | Shrike-Fi Three-Phase SPWM Inverter | https://github.com/Amaan9737/shrike-fi-three-phase-spwm-inverter |
| ANNESTIO PIETY CASTANHA | ShrikeFi 16-bit Multicycle CPU | https://github.com/apcetc/Vicharak_Campus_Fellowship_APC-/tree/main/PROJECT_1 |
| Nathan Mathews | Tiny ILA for Shrike | https://github.com/Deagle2/shrike-traces |
| Revand Pradeep | Shrike-Sentinel | https://docs.google.com/document/d/1DzsEX9RhsuA5Obxm0qkuIky-P2YCXNoWIiYl_c4sDtA/edit?usp=sharing |
| Saksham Sud | ShrikeFi BLE find-my-board tag (iBeacon + Find Me + last-seen map) | https://github.com/Geneticscrol/shrikefi-ble-tag |
| Saksham Sud | Perch — Passive Environmental Radio Census for ShrikeFi (receive-only 802.11 management-frame auditor) | https://github.com/Geneticscrol/perch |
| yatharth vishwa | OTA support for ShrikeFi's FPGA | https://github.com/yatharthvishwa/ShrikeFi_FPGAOTA |
| yatharth vishwa | ESP32-AndroidHID-Agent | https://github.com/yatharthvishwa/ESP32-AndroidHID-Agent |

### In Review (open PRs)
_None._

Full list + upstream examples: [docs/PROJECTS.md](docs/PROJECTS.md)
<!-- PROJECTS_END -->
