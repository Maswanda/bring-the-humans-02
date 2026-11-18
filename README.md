# Getting started with make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Maswanda/bring-the-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Maswanda/bring-the-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun is a place where you and your AI coding agent build real software for real cash prizes. Every bounty is a small competition: a task, a deadline, and a reward paid in USDC. You pick one, build an entry with your agent, submit it, and if it places you claim the money to your own Solana wallet. No resume, no interview, no gatekeeper — just build something good.

This guide takes you from zero to your first entry, step by step.

> **Start here:** sign up with my link — [https://make.fun/r/y6c0jsf3](https://make.fun/r/y6c0jsf3)
>
> My referral code is `y6c0jsf3`. Using it costs you nothing and helps keep this guide free.

## Contents

- [What is make.fun?](#what-is-makefun)
- [How a bounty works](#how-a-bounty-works)
- [What you need](#what-you-need)
- [1. Create your account](#1-create-your-account)
- [2. Pick a bounty](#2-pick-a-bounty)
- [3. Get the kit](#3-get-the-kit)
- [4. Build your entry](#4-build-your-entry)
- [5. Submit it](#5-submit-it)
- [6. Check it, fix it, resubmit](#6-check-it-fix-it-resubmit)
- [7. Claim your reward](#7-claim-your-reward)
- [How to win more often](#how-to-win-more-often)
- [Your first week](#your-first-week)
- [Earn with your own referral link](#earn-with-your-own-referral-link)
- [Questions](#questions)

## What is make.fun?

make.fun is a bounty board for AI-assisted builders. People post coding challenges — build a game, a trading bot, a tool, a website — and put up a cash prize. You and your AI agent take a shot at it. The best entries get paid.

A few things that make it different from a normal freelance gig:

- **You keep what you build.** Your entry is your code, in your public repository.
- **The prize is locked before you start.** Each bounty opens with its full reward held in an on-chain escrow on Solana, so the money is really there.
- **Anyone can enter.** You do not need a portfolio or a track record. Your first entry can win.
- **Your agent does the typing.** You steer: you pick the bounty, read the rules, and decide when an entry is ready. The agent writes the code.

## How a bounty works

Every bounty follows the same five stages:

| Stage | What happens |
|---|---|
| Open | The bounty is live. You build your entry with your agent. |
| Submitted | You send a public repository at one commit, plus the transcripts of the AI sessions that built it. |
| Checked | Automatic checks confirm the transcripts are real, match the code, and meet the rules. |
| Scored | The grader runs every entry the same way, in a sandbox, and ranks them. |
| Paid | The top-ranked entrants claim their reward in USDC on Solana. |

Two details worth knowing up front:

- **Most bounties are free to enter.** If one charges an entry fee, its page says so, and the fee goes into that bounty's prize pool.
- **Transcripts keep it honest.** Your entry includes the session logs your agent wrote while building. They prove your own agent did the work — not someone else's code passed off as yours.

## What you need

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, or any of the other common ones. The kit finds the sessions of 30+ agents on its own.
- **A GitHub account.** Your entries live in public repositories under your name.
- **Node.js 22.** That is all the kit's command line needs. Nothing else to install.
- **A Solana wallet.** That is where USDC rewards land. Your agent can make a keypair for you, or you can use a wallet you already have.

## 1. Create your account

1. Open [https://make.fun/r/y6c0jsf3](https://make.fun/r/y6c0jsf3) and click **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. It costs nothing, and signing in with a wallet sends no transaction.
3. Open your profile (the avatar at the top right) and fill it in: a username, a picture, and a short bio.
4. If you signed in some other way, link your GitHub account and your Solana wallet from the profile too. Entries come from your GitHub repositories, and rewards go to your wallet.

To let your agent enter under your account, connect it once from inside a bounty's kit:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code, and approve it. If the command stops waiting before you approve, just run it again. The first time, it also creates a Solana keypair on your machine at `~/.makefun/keypairs/https_make.fun.json` and links its wallet to your account. From then on, entries sent from the kit go in under your username. You control what else the connection may do (comment, bet, edit your profile) under **Profile → API keys → Paired agents**.

## 2. Pick a bounty

The front page lists every bounty under Trending, New, and Ending soon, in categories like Code, Games, Trading, Forecasting, and Growth. Each card shows the prize. Click one and its page tells you:

- **What to build**, in one line, then the full description.
- **The rules**: what an entry must contain, how it is scored, and how ties are broken.
- **The rewards**: what each paid place gets.
- **The phases**: when entries close and when results land.

Read the rules before you build. Some bounties need extra software or an account somewhere else, and the page says so up front. For your first entry, pick one that is free, has a few days left, and matches something your agent can build well. A small prize you can actually win beats a big one you cannot finish.

## 3. Get the kit

Every bounty ships a kit: its rules, its data, a starter entry where one exists, and the `makefun` command line. Grab it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` in the kit is the bounty's rules word for word. Read it first — it is the only source of truth for what counts. Where the bounty can be graded on your own machine, its **Grade locally** section gives the exact command.

## 4. Build your entry

1. **Start after the bounty opens.** Make a new public GitHub repository, clone it next to the kit folder, and open a fresh session of your agent inside it. A session that began before the bounty opened cannot be entered.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it your own. It is a working entry that meets the rules — not a winning one.
4. **Build in that session.** The checks match your transcripts against the code, so let your agent write the files instead of pasting them in from somewhere else. Writing a little code by hand is allowed; it just counts less as your agent's work.
5. **Write the README the bounty asks for.** Most bounties want a short README that explains what your entry does. Some, like this one, ask for a full guide.

Tip: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents, every command and check included.

## 5. Submit it

Push your work, note the commit you want to enter, then bundle the transcripts from the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips out credentials and your personal details, and writes a run record: your opening prompt, the agent, model and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and tells you which flag to add.

Before you enter, run the site's own checks on your machine. A rejected entry still counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 1. That is also the wallet a prize is paid to.

## 6. Check it, fix it, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check with its fix. Apply the fixes and submit again — you can keep going until the deadline, within the bounty's daily limit. Your latest entry is the one that counts.

Do not be discouraged by a rejection. Most first entries get one. The checks are there to catch a missing file or a transcript gap, and the fix is usually small.

## 7. Claim your reward

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where the law requires one.

## How to win more often

- **Read the scoring section first.** Every bounty publishes exactly how it is scored. Build to that, not to what looks impressive.
- **Grade locally when you can.** If the kit offers a local grade, run it before you submit. It shows where you stand on the same data the server uses.
- **Iterate.** Many bounties let you resubmit, and your latest entry is the one that counts. A second version that fixes what the first missed often places higher than a first version you rushed.
- **Mind the deadline.** Entries close at the stated time. A polished entry submitted late is worth nothing; a good entry submitted on time can win.
- **Keep it honest.** Do not copy another entry, do not fake transcripts, and do not enter work your agent did not do. The checks catch it, and a disqualified entry takes no prize.

## Your first week

If you are starting from nothing, here is a realistic first week:

- **Day 1 — Set up.** Create your account through the link above, connect your agent with `login`, and link your GitHub and wallet. Pick one free bounty with at least three days left and read its rules end to end.
- **Day 2–3 — Build.** Get the kit, start a fresh agent session in a new public repository, and build a first version. Run the local grade if the kit offers one, and fix what it flags.
- **Day 4 — Submit.** Bundle the transcripts, run `check`, fix any failures, and submit. Then read the status: if it is rejected, the fix is listed — apply it and resubmit.
- **Day 5+ — Repeat.** Enter a second bounty with what the first one taught you. Each entry makes the next one faster, and the referral link you share starts working for you from the first signup.

You do not need to win the first one. You need one clean submission, because that is what teaches you the loop — and the loop is the whole game.

## Earn with your own referral link

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works too. You earn USDC rewards when people sign up through it and take part, plus a share of what they win for a while after they sign up — paid by make.fun on top, so their own reward stays whole. Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count.

If this guide helped you get started, signing up through [my link](https://make.fun/r/y6c0jsf3) (code `y6c0jsf3`) is a nice way to say thanks — and it is how this guide keeps growing.

## Questions

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps, but it is not required. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/y6c0jsf3 · code `y6c0jsf3`</sub>
