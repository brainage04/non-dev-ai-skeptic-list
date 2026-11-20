# non-dev-ai-skeptic-list

A curated list of X (Twitter) accounts that complain about AI usage **in software development** while not being software developers themselves. The blocklist equivalent of "BLOCKED" energy, minus the vibing coders.

Sparked by [this post](https://x.com/brainage19/status/2122988819222048802) (18 Nov 2026): "Someone should make a blocklist for non-software developers complaining about AI usage in software development." So we did.

## What qualifies an account

An account is listed only when **both** predicates hold, and every entry carries its evidence:

1. **Predicate A - complains about AI in a software-development context.** Not AI art. Not general AI doom. The complaint has to target AI-assisted or AI-generated *code* (vibe coding, Copilot-style tooling, AI code review, "AI is replacing software engineers", etc.).
2. **Predicate B - is not a software developer.** No evidence of writing software professionally or as a serious pursuit: no software/engineering job in bio or display name, no GitHub on X profile or personal site, no practitioner voice ("my PR", "our codebase"). Practitioners complaining about AI tooling are *excluded* - they have skin in the game.

Excluded by design: software engineers, CS students, founders who build, QA, data scientists, and anyone whose complaint is practitioner frustration rather than outsider sneering. Boundary classes (researchers, engineering managers, ex-devs) go to human review, not the list.

Every account in `blocklist.csv` has a matching line in `evidence.jsonl` with the post text, the bio at review time, and the verdict reasoning.

## Files

| File | What it is |
|---|---|
| `blocklist.csv` | `username,display_name,evidence_post` - one row per listed account |
| `evidence.jsonl` | Full decision record for every account reviewed, listed or not |
| `README.md` | This document: criteria, method, appeals |

## How to use it on X

X has no native block-list import anymore. The maintained community path is the [XActions Block List Manager](https://xactions.app/scripts/block-list-manager) console script:

1. Open [x.com](https://x.com) logged in, press F12, open the Console.
2. Paste the script from the XActions page (it is readable JS; nothing is sent anywhere).
3. Run: `importBlockList(["user1","user2"])` with the handles from `blocklist.csv`.

At ~2-3 s per account, a few hundred entries take under half an hour. The script only clicks Block through the normal UI; it never sends your credentials anywhere.

## Appeals

Wrongly listed? Open a GitHub issue titled `appeal: @handle` with either:

- evidence you write software professionally (a GitHub, a company page, a repo), or
- the post we cited, in context, read as something other than a non-dev complaint.

Removals land in the next commit and in the changelog below. We would rather have an empty list than a wrong one.

## Method (short version)

Verdict values in `evidence.jsonl`: `listed` (on the list), `review` (awaiting the owner's call; used for boundary classes and for accounts whose post text needs thread context to show predicate A; carries a `reviewReason` saying what the owner is deciding), `dev-excluded` (developer evidence found), `not-candidate` (fails a predicate), `not-listed` (passed the predicates but the owner declined listing after review).

1. Candidates come from reply/quote harvests around AI-in-dev posts and from logged-in X keyword searches (dev-context phrases: "vibe coding" + "technical debt", "AI slop" + "codebase", etc.). No paid API use.
2. Each candidate gets a pass-A check (is the complaint about AI *in software development*?) from the post text.
3. Pass-B checks for developer evidence: bio/display name regex, then bio links, then the linked website scraped for a GitHub, then exact-username GitHub probes. Any solid dev evidence excludes the account.
4. Remaining accounts get a human read. Nobody lands on the list from automation alone.

The full run log for the pilot harvest (18-19 Nov 2026) is in `evidence.jsonl`.

## Changelog

- 2026-11-19: pilot. 1 listed, 4 in human review, 3 dev-excluded, 6 not-candidates.
- 2026-11-19: owner lead (Sh4de0 Frameless Portals thread). 2 listed (V2_Ultrakill_, _potatobag), 2 not-candidates (the mod author and a pro-AI reply). 3 listed total.
- 2026-11-20: owner verdict: 4 review accounts not listed (GuptaBioDD, ZidaneZ08902030, moonseesyou, GaryMarcus).
- 2026-11-20: harvest of two owner posts (read-the-code, luddite-fatigue) + meowajor lead. 11 listed, 7 review, 1 dev-excluded, 1 not-candidate. 14 listed total.
- 2026-11-20: diff-review corrections. 8 listed accounts downgraded (7 to review: post text needs thread context or shows a practitioner signal; 1 to not-candidate), 4 review accounts to not-candidate; postUrl added to every record; CSV rewritten with LF endings. 6 listed total.
- 2026-11-20: re-review corrections. taiping_rebel moved to review (same no-AI-in-text shape as the others); _potatobag predicate fields aligned; note cleanup. 5 listed total.
