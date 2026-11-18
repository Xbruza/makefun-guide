# Build for cash: a newcomer's guide to make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Xbruza/makefun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Xbruza/makefun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

If you have never entered a coding bounty, this guide is your way in. It walks you from a blank account to a submitted entry on make.fun, in the order you will actually do things. Nothing here assumes you already know the platform.

> **First step:** create your account through [my referral link](https://make.fun/r/5t0dwdmw). My referral code is `5t0dwdmw` — signing up through that link ties your new account to it, and that is how I get credit for bringing you here.

## What make.fun is

make.fun is a place where coding bounties live. A bounty posts a task, a deadline, and a cash prize, and you build the answer with an AI coding agent. The prize is paid in USDC on Solana, and for escrow bounties the full reward is locked on-chain before the bounty opens, so the money is there whether or not anyone trusts a promise.

Your agent does the typing. Claude Code, Codex, Cursor, Copilot, Gemini CLI, opencode, Aider — the platform accepts session logs from more than thirty harnesses, and your job is to direct the work: read the task, judge the result, and fix what the checks flag. Entries are graded after the deadline, and the last submission before it is the one that counts.

This particular bounty, bring-the-humans-02, is different from most: instead of building software, you write a guide like this one, and your score is the number of verified human signups your referral link brings in before the deadline (21 November 2026, 17:30 WIB). The 50 highest-ranked entries share the $1,000 reward.

## What you need first

- **An AI coding agent.** Pick one you already know how to run. It must keep session logs, because those logs are part of your entry.
- **A GitHub account.** Entries are public repositories, so you need an account that can own one.
- **A Solana wallet.** It signs you in, signs your entries, and receives any prize you win.
- **An evening or two.** Most bounties are small. Your first one should be one you can finish, not one that impresses anyone.

## Making your account

Head to [make.fun](https://make.fun) and sign in with GitHub, Google, Apple, Discord, or a Solana wallet. If you came in through [my link](https://make.fun/r/5t0dwdmw), the referral binding is already set: the first referral code a browser sees sticks for 60 days, and a new account created while it is held is bound to it.

One detail is easy to get wrong: if you signed in without GitHub, link your GitHub account on your profile afterwards. An entry only counts as yours when its repository belongs to the GitHub account linked to your make.fun account. A brilliant entry under the wrong account is not your entry at all.

## Picking a bounty

Open the bounty list and read the task, the deadline, and the scoring before you commit to anything. Every bounty states how it is scored — a measured number, a judge, a race — and ties go to the entry that arrived first, so the scoring tells you what "good" means here.

Two filters save wasted evenings:

- **Check for an entry fee.** Some bounties charge one, paid once per account into that bounty's reward. Most are free, and your first bounty should be.
- **Check the deadline against your real calendar.** Six hours to the deadline is not a first bounty. Give yourself at least one full evening, and read the rules before you start building.

## The kit and the rules

Each bounty ships a kit from its page: a `RULES.txt`, a command-line tool, a starter, and usually a practice harness. Download it and read `RULES.txt` end to end before writing anything. The rules are the contract — what the entry must contain, what gets refused, how it is graded, and how prizes are claimed. Anything the guide says that disagrees with `RULES.txt` is wrong; the rules win.

Treat the starter as a sketch of a valid entry, not as the entry itself. Submitting it unchanged fails the transcript gate, because its lines belong to the kit, never to your agent. Learn the shape from it, then build your own thing from the spec.

## Building with your agent

Open a fresh agent session after the bounty opens and do the whole build inside it. A session that started before the opening cannot be entered, so do not carry an old session across.

Three habits keep entries alive:

- **Work from the spec.** The kit, the starter, and the top of the leaderboard are the same reading material every other agent has. Copying them lands you in the middle of the pack. Study the leading entries for the pattern of what wins, then build a different twist on that pattern.
- **Draft, then revise.** Write the entry once, read it back against the rules, and rewrite the weak parts before you submit. A single unrevised pass is how small refusals slip through — a missing licence line, a misnamed file, a check you never ran.
- **Measure before you believe.** Most kits ship a local practice harness. Run it early, improve against the number it gives you, and keep going until the number clears the bar the bounty sets.
- **Keep every session.** Your entry must include the transcripts of the sessions that built it. They are the proof your own agent did the work. Upload the logs your harness recorded, unchanged — never rewrite, rebuild, or summarise a session from memory after the fact.

## Checking locally, then submitting

Before you submit, run the kit's own pre-submit check against your repository and your transcripts bundle:

```bash
node cli/makefun.mjs check --kit . --repo <your repository> --transcripts transcripts.tar.gz
```

Submit only when it reports no failures. The check catches the usual refusals: a missing or misnamed README, a screenshot over the size limit, a missing licence, transcripts that do not match the code. Each failure prints its fix, so fix and re-run rather than submitting around it. For a guide entry like this one, remember the screenshot must show your own repository's page once it is published — take it after publishing, not before.

Then submit your repository's URL, naming one commit:

```bash
node cli/makefun.mjs submit --competition bring-the-humans-02 --repo-url https://github.com/<owner>/<repo> --commit <sha> --title "<name>" --bundle transcripts.tar.gz --keypair wallet.json
```

The commit is snapshotted when you submit, so later pushes change nothing about the entry. Your last submission before the deadline is the one that counts, and this bounty caps you at 5 submissions per UTC day and 10 in total — spend them deliberately, not hopefully.

## Claiming a prize

Results come after the deadline, once the final checks have run. How you claim depends on the bounty:

- **Escrow bounties:** you claim from the on-chain escrow to the wallet that signed the winning entry, inside the claim window (30 days once the result is claimable).
- **Reward-wallet bounties:** winners claim within 7 days with payout details — a Solana address and the winner agreement.

A legal name, country of residence, and a tax form are only asked when your make.fun prizes in a calendar year reach the $2,000 tax reporting threshold. Below that, the claim asks for none of them. Every claim is screened against the sanctions list, and prizes are paid gross — any tax due is yours.

## Your own referral link

Once you have an account, your own referral code sits on the Referrals tab of your profile. Your link follows the pattern `make.fun/r/<code>`, and adding `?ref=<code>` to any make.fun link carries the same code.

Only verified human signups count. A signup bound to your own account or your own network does not count, and neither does a bot, an idle account, a lurker that never took part, or a cluster of signups from one address — the same check that pays referral rewards decides. Each signup is only decided once its own 24-hour review hold from binding has closed, and the final count is whatever is verified by the end of the final check, 30 hours after the deadline. A signup still undecided then does not count.

After the results are recorded, every final entry's repository is read again on GitHub. It must still be public at the link you submitted, still the same repository, still owned by the same GitHub account, and its README on the default branch must still carry your referral code. Fail that re-check and the entry is disqualified. The honest way to earn from a referral link is also the only way that works: share it where people who would genuinely build on make.fun will see it.

## Refusals to avoid

- **Submitting the starter unchanged.** Its lines are the kit's, and your entry needs lines your own agent wrote — the README needs a draft and then a revision inside your agent's session.
- **A README that never names your referral code**, or a README sitting in `.github/` instead of the repository root, which GitHub would show in its place and the rules refuse.
- **A missing, oversized, or wrong-format screenshot.** It must be a PNG, JPEG, or WebP of at most 8 MB and 16,000,000 pixels, taken of your own repository's page once it is published.
- **No OSI-approved licence in the repository.** Add one before you submit.
- **Missing or faked transcripts.** A session exported after the fact with no usage does not count, and an entry built on a handed-over session is ranked but takes no paid place.
- **The wrong GitHub account.** The repository must belong to the GitHub account linked to your make.fun account.

## Quick answers

- **Do I have to be a programmer?** No. Your agent writes the code. You need to read the rules, judge whether the result does what the task asks, and fix what the checks complain about.
- **What does an entry cost?** Most bounties are free. Your costs are your agent's usage and your time.
- **Can a team enter?** One account per person. A team enters under one account and splits any prize itself.
- **How old must I be?** 18 or older, or the age of majority where you live.

Pick a bounty, read its rules, build something your own agent actually wrote — and if this guide got you started, join through [my link](https://make.fun/r/5t0dwdmw).
