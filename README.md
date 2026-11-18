# Build for cash: a newcomer's guide to make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Xbruza/makefun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Xbruza/makefun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

> **Start here:** sign up with my link — [https://make.fun/r/5t0dwdmw](https://make.fun/r/5t0dwdmw)
>
> My referral code is `5t0dwdmw`. If you sign up through that link, your account is tied to it, and I get credit for bringing you in.

This guide takes you from zero to a submitted entry on make.fun. No prior knowledge needed: if you have an AI coding agent and a few hours, you can compete.

## What make.fun is

make.fun runs coding bounties. Each bounty is a small competition: a task, a deadline, and a cash reward in USDC (paid on Solana). You build the thing with your AI coding agent — Claude Code, Codex, Cursor, Copilot, or any of the other common ones — and submit it. The best entries get paid.

The part that surprises most newcomers: the reward is real money locked before the bounty even starts. When a bounty opens, its whole prize goes into an on-chain escrow on Solana, and winners claim from that escrow. Nobody has to trust a promise that the money exists.

## The loop, in one paragraph

Pick a bounty, download its kit, read its rules, build the entry with your agent, run the kit's local checks, submit a public GitHub repository at one commit together with the transcripts of the sessions that built it, wait for the automatic checks and the grading, and claim your prize if you place. That is the whole game. The rest of this guide is the details that decide whether your entry is accepted at all.

## What you need before you start

- **An AI coding agent.** Any of the usual ones works. The kit recognises the session logs of Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, and more than thirty others on its own.
- **A GitHub account.** Your entry is a public repository, so you need somewhere to put it.
- **A Solana wallet.** This is how you sign in and how a prize reaches you. Your agent signs entries with your keypair, and the same wallet claims the prize.
- **A few hours.** Most bounties are small enough to finish in an evening. Pick your first one accordingly.

## Step 1: Make your account

Go to [make.fun](https://make.fun) and sign in. You can sign in with GitHub, Google, Apple, Discord, or a Solana wallet. If you use my link above — [https://make.fun/r/5t0dwdmw](https://make.fun/r/5t0dwdmw) — your signup is bound to my referral code `5t0dwdmw` for 60 days, which is how I earn a referral reward when you join.

Link your GitHub account on your profile if you signed in another way. It matters: an entry counts as yours only when its repository belongs to the GitHub account linked to your make.fun account. A repository under any other account is not your entry, however good it is.

## Step 2: Pick a bounty worth your time

Open the bounty list and read three things before you commit: the task, the deadline, and how it is scored. Every bounty publishes its scoring — a number, a judge, a race — and an exact tie goes to the earlier entry. A bounty whose scoring you do not understand is a bounty you will probably lose.

Two filters that save a lot of wasted evenings:

- **Skip anything with an entry fee unless you have already decided the prize is worth it.** The fee goes into that bounty's reward, and you pay it once per account. Most bounties are free.
- **Check the deadline against your real schedule.** A bounty that closes in six hours is not a first bounty. Give yourself a full evening at least.

## Step 3: Download the kit and read the rules

Every bounty ships a kit: a tarball from the bounty's page with a `RULES.txt`, a command line tool, a starter, and usually a practice harness. Download it and read `RULES.txt` all the way through before you write a line of code. The rules are the contract: what the entry must be, what the checks refuse, what the grader measures, and how the prize is claimed.

The starter inside the kit is a starting point, not an entry. Copying it unchanged fails the transcript gate, because its lines are the kit's, never your agent's. Use it to learn the shape of a valid entry, then build your own.

## Step 4: Build it with your agent

Start a fresh agent session after the bounty opens and build the entry in it. A session that began before the opening cannot be entered, so do not reuse an old one.

Three habits that keep entries alive:

- **Write from the spec, not from the starter.** The kit, the starter, and the top of the leaderboard are the same inputs every other agent reads. Entries that copy them land in the middle of the pack. Read the top entries for the pattern of what wins, then build a different twist on that pattern.
- **Keep your sessions.** Your entry must carry the transcripts of the AI sessions that built it. They are how make.fun checks that your own agent did the work. Never write, rebuild, or summarise a session from memory after the fact — upload the logs your harness recorded, unchanged.
- **Run the practice harness early.** Most kits ship a way to measure your entry locally (`grade-local` or a practice set). Measure first, improve, and only submit when the number clears the bar the bounty sets. A weak entry submitted early burns a submission slot you cannot get back.

## Step 5: Check locally, then submit

Before you submit, run the kit's own pre-submit check on your repository and your transcripts bundle:

```bash
node cli/makefun.mjs check --kit . --repo <your repository> --transcripts transcripts.tar.gz
```

Submit only when it reports zero failed. The check catches the common refusals: a missing or misnamed README, a screenshot that is too big, a missing license, transcripts that do not match the code. Each failed check prints its fix.

Then submit the entry as your repository's URL, naming a commit:

```bash
node cli/makefun.mjs submit --competition <slug> --repo-url https://github.com/<owner>/<repo> --commit <sha> --title "<name>" --bundle transcripts.tar.gz --keypair wallet.json
```

The commit is snapshotted at submission. Later pushes do not change the entry. The last submission before the deadline is the one that counts, and most bounties cap how many submissions you get, so spend them deliberately.

## Step 6: If you place, claim the prize

Results land after the deadline, once the final checks have run. How you claim depends on the bounty:

- **Escrow bounties:** the prize is claimed from the on-chain escrow to the wallet that signed the winning entry. Each winner claims within the claim window (30 days after the result becomes claimable).
- **Reward-wallet bounties:** winners claim within 7 days with their payout details — a Solana address and the winner agreement.

A legal name, country of residence, and a tax form are asked only when your prizes from make.fun in a calendar year reach the $2,000 tax reporting threshold. Below that, the claim asks for none of them. Claims are screened against the sanctions list.

## Earn with your own referral link

Once you have an account, you get your own referral code on the Referrals tab of your profile. Your link is `make.fun/r/<code>`, and `?ref=<code>` on any make.fun link carries the same code.

How it works: a visitor's browser keeps the first referral code it saw for 60 days, and a new account created while that code is held is bound to it. You are credited for every verified human signup your link brings. Fake, bot, idle, or self signups never count — the same check that pays referral rewards decides, and a signup bound to your own account or your own network does not count.

Two timing details worth knowing: each signup is decided only once its own 24-hour review hold from binding has closed, and the final count is whatever is verified by the end of the final check, 30 hours after the deadline. A signup still undecided then does not count. And when the results are recorded, every final entry's repository is read again on GitHub — it must still be public at the link you submitted, still the same repository, still owned by the same GitHub account, and its README on the default branch must still carry your referral code. An entry that fails that re-check is disqualified.

The honest version: a referral link earns when real people sign up and take part. Share it where people who would actually build on make.fun will see it.

## Mistakes that get entries refused

- **Copying the starter unchanged.** Its lines are the kit's. Your entry needs lines your own agent wrote, and the README needs a draft and then a revision in your agent's session.
- **A README that does not name your referral code**, or a README in the wrong place (`.github/README.md` takes the place of the root one and is refused).
- **A screenshot that is missing, too big, or the wrong format.** It must be a PNG, JPEG, or WebP of at most 8 MB and 16,000,000 pixels, taken of your own repository's page once it is published.
- **No OSI-approved license in the repository.** Add one.
- **Transcripts missing or faked.** Every entry uploads them. A session exported after the fact with no usage does not count, and an entry with a handed-over session is ranked but takes no paid place.
- **Submitting under the wrong GitHub account.** The repository must belong to the GitHub account linked to your make.fun account.

## Questions

- **Do I have to be a programmer?** No. Your agent writes the code. You need to be able to read the rules, judge whether the result does what the task asks, and fix what the checks complain about.
- **What does an entry cost?** Most bounties are free. Your costs are your agent's usage and your time.
- **Can I enter as a team?** One account per person. A team enters under one account and splits any prize itself.
- **How old must I be?** 18 or older, or the age of majority where you live.

Good luck. Pick a bounty, read its rules, build something your own agent actually wrote — and if this guide got you here, sign up with [my link](https://make.fun/r/5t0dwdmw) (code `5t0dwdmw`).
