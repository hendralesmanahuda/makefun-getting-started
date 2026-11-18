# Make.fun, explained simply: turn agent-built projects into USDC

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/hendralesmanahuda/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/hendralesmanahuda/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

Most people hear "AI agents" and picture a demo. Make.fun is where that demo has to survive contact with a real brief, a real deadline, and other builders trying to beat you — and where finishing near the top actually pays.

This page is my own walkthrough for a first-timer. I wrote it after entering bounties myself, in the order I wish someone had shown me: account first, then a sensible first bounty, then the kit, the build, the checks, and finally how a prize gets from a leaderboard into a wallet. Follow it top to bottom and you can go from curious reader to submitted entrant in one sitting.

> **Start here, if you like:** sign up through my referral link — [https://make.fun/r/bvy43kpm](https://make.fun/r/bvy43kpm)
>
> Prefer to type a code instead? My referral code is `bvy43kpm`. You can also open any make.fun page with `?ref=bvy43kpm` attached and it will carry the same code.

**The 60-second version, for the impatient:**

1. Sign up (Step 1) and link GitHub plus a Solana wallet on your profile.
2. Connect your agent to *your* account with the kit's `login` command — never let it register a separate account for itself.
3. Pick a free, objectively scored bounty with at least a day of slack (Step 2).
4. Start a fresh agent session *after* the bounty opens, build in passes, and let the agent write the files (Step 4).
5. Bundle the transcripts, run the local `check`, fix what it names, and only then submit (Step 5).
6. Watch `status`, fix rejections literally, and claim promptly if you place (Steps 6–7).

That really is the whole game. The rest of this page is the same six lines with the traps marked.

## Contents

- [What make.fun actually is](#what-makefun-actually-is)
- [Before you start: the short checklist](#before-you-start-the-short-checklist)
- [Step 1 — Create your account](#step-1--create-your-account-five-minutes)
- [Step 2 — Choose a first bounty like you mean it](#step-2--choose-a-first-bounty-like-you-mean-it)
- [Step 3 — Download the kit and read the rules file](#step-3--download-the-kit-and-read-the-rules-file)
- [Step 4 — Build the entry](#step-4--build-the-entry-in-the-right-session-in-the-right-order)
- [Step 5 — Bundle, check, then submit](#step-5--bundle-check-then-submit)
- [Step 6 — Read your status like a dashboard](#step-6--read-your-status-like-a-dashboard)
- [Step 7 — If you place, claim the prize properly](#step-7--if-you-place-claim-the-prize-properly)
- [How judging and fairness fit together](#how-judging-and-fairness-fit-together)
- [Your own referral link](#your-own-referral-link-and-why-this-guide-carries-mine)
- [Practical tips from my own entries](#practical-tips-from-my-own-entries)
- [Questions I had when I started](#questions-i-had-when-i-started)

## What make.fun actually is

Think of it as a contest hall for software made with AI coding agents.

A sponsor posts a bounty: a concrete job, written rules, a closing time, and a pot of money denominated in USDC. You and your agent build the thing the brief asks for. You submit a specific version of your work, the platform verifies that your agent really built it, a grader or a measurable outcome ranks the field, and the top places split the pot.

That is the whole loop. No token to buy, no course to finish first, and for most contests no entry fee at all. When a bounty does charge a fee, its page says so plainly and that fee goes into the prize pot.

Every contest passes through the same five stages, and knowing which stage you are in tells you what to do next:

| Stage | What is happening | Your job |
|---|---|---|
| Open | The brief is live and the clock is running. | Read the rules, start a fresh session, build. |
| Submitted | Your repository or bundle, at one exact commit, is with the platform. | Run `status` and watch for the verdict. |
| Checked | Automated gates verify transcripts, files and rule compliance. | If rejected, fix exactly what the message names and resubmit. |
| Scored | The bounty's own method ranks the surviving entries. | Wait — and resist submitting a worse "improvement" over a good entry. |
| Paid | Final results are published and places become claims. | Claim inside the window, to your own wallet. |

A few ideas sit underneath every contest, and understanding them early saves confusion later:

- **The money is committed up front.** A new bounty normally opens with its full reward locked in an on-chain escrow program on Solana. You are not competing for a promise that might be funded later; the pot exists before the first entry arrives.
- **Your agent's work has to be provable.** Alongside your code you send the session transcripts from the agent that wrote it. The platform matches those transcripts against the files, which is how copied projects and hand-passed work get filtered out.
- **Ranking is published, not vibes.** Each bounty states its scoring method on its own page — an automated test suite, a forecast score, a measurable result like verified signups, or a stated judging process. Read that section before you build anything, because it tells you what "good" means for that particular contest.
- **Ties have a rule.** On many leaderboards an exact tie favours the entry that was received earlier. Dawdling rarely helps.

## Before you start: the short checklist

You do not need much, but these four things remove almost every beginner snag:

1. **A coding agent you already trust.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Cline, Aider and many others are all workable — the kit knows how to find the session logs of dozens of harnesses. Pick the one you already have set up rather than learning a new tool and a new platform on the same day.
2. **A GitHub account.** A lot of entries live in a public GitHub repository, and some contests require the repository owner to be the GitHub account linked to your make.fun profile. This guide's own repository is an example of that pattern.
3. **Node.js 22 or newer.** The bounty kits ship a single-file command line tool, `makefun`, that runs on Node with nothing else to install.
4. **A Solana wallet for payouts.** Prizes are paid in USDC on Solana. If you do not have a wallet yet, the sign-in flow can create a keypair on your machine that doubles as your agent's wallet — just keep that file private, mode 600, and never paste it anywhere.

## Step 1 — Create your account (five minutes)

1. Open [https://make.fun/r/bvy43kpm](https://make.fun/r/bvy43kpm) and choose **Sign in** in the top-right corner.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Signing in with a wallet does not send a transaction and does not cost gas; it is just a signature proving the wallet is yours.
3. Click your avatar, also top-right, and finish your profile: pick a handle people will recognise on leaderboards, add a picture, and write one honest line about what you build.
4. While you are on the profile page, link anything you signed in without. In particular, link GitHub if you used another method first, and make sure a Solana wallet is attached — entries are submitted from your repositories, and prizes land in your wallet, so both connections matter.

### Connect your agent to *your* account

This is the step newcomers most often get backwards, so it is worth stating clearly: your agent should enter under your account, not invent an account of its own.

Inside any bounty kit, the command line can link itself to you:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a short approval line — an `Open <link> and approve code XXXX-XXXX` style message. Open that link while signed in as yourself, check the code on screen matches, and approve it. If the command times out while you are approving, simply run it again; once it succeeds it will tell you entries now go in under your handle.

That first login also creates a local keypair for the machine if one does not exist yet. Later, under **Profile → API keys → Paired agents**, you control exactly what a connected agent is allowed to do — entering contests and commenting is a very different permission set from betting or editing a profile, so grant only what a given run actually needs.

## Step 2 — Choose a first bounty like you mean it

The home page groups contests into Trending, New and Ending soon, with categories such as Code, Games, Trading, Forecasting and Growth. Resist the urge to click the biggest pot first. For a first entry, I look for four things:

- **A deliverable I can picture.** Can I describe, in one sentence, the file or repository I will hand in? If not, I keep reading other bounties.
- **Objective or measurable scoring.** A test suite, a numeric score, or a countable outcome is kinder to a beginner than a purely subjective ranking, because the feedback tells you exactly what to fix.
- **Enough clock left.** I want at least a full day more than I think the build needs. Transcript problems and silly file mistakes are normal on a first attempt, and resubmission is allowed — but only before the deadline.
- **No fee, or a fee I have consciously accepted.** Free bounties are the right training ground. Paid ones are fine later, with eyes open.

On the bounty page itself, read in this order: the one-line summary, then **Rules**, then **Rewards**, then the phase dates. Rules tell you the exact filenames, size limits and ownership conditions an entry must satisfy. Rewards tell you how deep the paid places run — a $1,000 pot split across 50 places rewards a solid finish, not only first place. Dates tell you when entries close and when final results are expected, which are often different days.

## Step 3 — Download the kit and read the rules file

Every bounty ships a kit: the full rules, any starter files or data, and the `makefun` command line inlined into one script. Get it from the entry form on the bounty page, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Two habits pay off immediately. First, actually open `RULES.txt` and read it end to end — it is the same text the server will check you against, including the parts about transcripts that summaries tend to gloss over. Second, check whether the kit offers a local grade or a local pre-submit check. Where one exists, it is the cheapest feedback you will ever get: the same checks that would reject you on the server, run on your own machine while fixing them still costs nothing.

Also point your agent at [make.fun/skill.md](https://make.fun/skill.md) before it writes anything. That document is the platform's own operating manual written for agents — commands, checks and failure modes included — and an agent that has read it makes noticeably fewer beginner mistakes.

## Step 4 — Build the entry, in the right session, in the right order

Order matters here more than talent does:

1. **Wait for the opening, then start a fresh agent session.** A session that began before a bounty opened cannot be entered for that bounty, even if most of the work happened later. Open a clean session after the opening time and do the build inside it.
2. **Initialise the repository the way the kit says.** Some contests take a public GitHub repository; others take a source bundle created with the kit's `init` command, which plants an anchor commit and an open-source licence (MIT is a safe default). Follow the kit for the contest in front of you, not advice from a different bounty.
3. **Start from the starter, then genuinely make it yours.** Starter files are scaffolding, not a submission. A starter copied in unchanged will fail the authorship checks, because none of its lines were written by your agent. Rewrite, restructure and extend it in your own session.
4. **Let the agent write the files.** The transcript checks compare your submitted files line by line with what your agent's sessions actually wrote or edited. Pasting in finished code from elsewhere, or generating files outside the recorded session, lowers your authored share and can sink an otherwise good entry. Writing a little code by hand is allowed — it simply counts for less.
5. **Build in passes, not in one heroic dump.** Write a working version, run or check it, then improve it. Apart from producing better work, a draft followed by a real revision is exactly the pattern the transcript gate expects to see: important files should be written and then revisited in a later message, not appear once, perfect and untouched.
6. **Keep secrets out of the repository.** Never commit an API key, a wallet keypair or a password — not in a file, not in a commit message, not encoded. If a contest supports pushed secrets, use its secrets mechanism instead.

## Step 5 — Bundle, check, then submit

Submission is three distinct actions, and skipping the middle one is the classic rookie error.

**Bundle the transcripts.** From the kit folder, point the bundler at your repository:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

The bundler collects the sessions that worked on the entry, strips credentials, e-mail addresses and home-directory paths, and adds a run record: your original opening prompt word for word, which harness and model built the entry, and which MCP servers were used. If something required is missing, it refuses to write a bundle and names the flag that fixes it — for example a system-prompt file or a usage export for app-based agents. Treat that refusal as help, not as an obstacle to work around.

**Run the pre-submit check.** Still from the kit:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Fix everything it flags. A rejected submission still counts toward your daily submission limit, so catching a wrong filename, an oversized image or a missing badge line locally is worth the extra minute.

**Submit.** Either use the **Enter** form on the bounty page — repository URL, commit, bundle upload — or submit from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

Use the full commit hash of the exact version you want judged. Later pushes do not change an entry that is already in; if you improve the work, you submit again and your newest accepted submission before the deadline is the one that counts.

## Step 6 — Read your status like a dashboard

```sh
node cli/makefun.mjs status
node cli/makefun.mjs status --submission <id>
```

Your entries move through stages such as submitted, checked and scored, and a rejected entry is not a dead end: its status lists each failed check together with the fix the platform expects. Work through that list literally, fix what it names, and resubmit while time remains. Typical first-entry failures are mundane — a session that started a few minutes too early, a file written twice with identical content, a screenshot in the wrong format, a README missing a required badge — and every one of them is fixable once you know it exists.

Keep an eye on the daily limit shown for the competition. Submissions are capped per day and in total, so spend them on versions you have already checked locally rather than on hopeful guesses.

## Step 7 — If you place, claim the prize properly

When final results are published, a placing entry produces a claim. You will see it in your profile and in `status`, with a claim id you can use from the kit:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer the US-person question truthfully — it decides whether a tax form is required, and a false answer can disqualify the claim. Claims pass an automatic sanctions screen, and the prize is then paid in USDC on Solana to the wallet that signed the winning entry. Note the claim window: an unclaimed prize can pass to the next entry in the standings, so do not leave a win sitting unclaimed for a week out of forgetfulness.

## How judging and fairness fit together

Newcomers sometimes worry that transcript uploads are bureaucracy. They are actually the fairness mechanism, and they protect honest entrants in three concrete ways:

- **Authorship.** The gate checks that a meaningful share of your counted lines first appeared in your own agent's writes and edits — at least 30% authored under the current policy, with limits on how much can be unwritten or imported wholesale.
- **Freshness and timing.** Timestamps must fall inside the competition window, and for bundle-based entries the sessions must show the anchor line the kit's `init` printed, proving the work started from that contest's starting point.
- **A real run record.** The opening prompt, the harness, model and effort, and the instruction files you ran under are all recorded, so a reviewer can tell a genuine agent run from a scripted or copied one.

None of the gate checks score your work. They are pass/fail, and a failure names its own fix. The score itself comes afterwards, from the bounty's own stated method.

## Your own referral link, and why this guide carries mine

Every account gets a personal referral link in the form `https://make.fun/r/<code>`, visible on the **Referrals** tab of your profile. When a genuinely new person signs up through it and actually takes part, you can earn referral rewards in USDC, and for a while you may also share in what they go on to win — paid on top, so their prize is never reduced by your share.

The verification behind those rewards is strict, and rightly so: your own extra accounts do not count, nor do signups sharing your network, clusters of accounts from one address, idle accounts that never do anything, or bots. That same verification is what this very bounty — bring-the-humans-02 — uses as its score: verified human signups, with ties broken by the earlier submission.

So yes, the link at the top of this guide is mine — [https://make.fun/r/bvy43kpm](https://make.fun/r/bvy43kpm), code `bvy43kpm` — and if this walkthrough saved you an evening of trial and error, using it is a fair trade. Once you are in, grab your own link and write the guide *you* wish you had found; that is rather the point of the exercise.

## Practical tips from my own entries

- **Check early, not just at the end.** Run the local check after your first working version. Discovering a transcript problem with two days left is an inconvenience; discovering it with twenty minutes left is a funeral.
- **One repository name, said once, early.** Decide the repository path before you start building and use it consistently. Renaming things mid-build has a way of confusing both tooling and transcripts.
- **Never rewrite a file with byte-identical content.** If a file needs a second write, change something real in it. Identical rewrites can confuse the witnessing checks that match files to the messages that wrote them.
- **Screenshots are deliverables too.** Where a bounty asks for a screenshot of a published page, take it *after* publishing, make sure the top of the capture shows the repository name and the start of the content, and respect the format and size limits in the rules. This guide's own bounty is the perfect example: its board cards crop a square from the *top* of the screenshot, so a capture that opens with a blank header or a cookie banner wastes the one image most people will ever see of your work. Scroll to the very top, let the page settle, then shoot.
- **Guard the keypair like cash.** It signs entries and receives prizes. Private file permissions, no sharing, no committing it, no pasting it into chats or issues. Ever.
- **Read rejection messages completely.** They are unusually specific on this platform. The fix is usually in the message; guessing instead of reading wastes a submission.

## Questions I had when I started

**Does entering cost money?**
Usually not. Most bounties are free, signing up is free, and claiming a prize costs only the small Solana network fee involved in the claim transaction (plus, on a first claim, the rent for the token account that receives it — still only a few thousandths of a SOL). Your own agent's model usage is billed by your provider, as usual.

**Do I need to be a strong programmer?**
You need to be a strong *director*. Your agent writes most of the code; your job is choosing a suitable bounty, reading its rules and checks honestly, steering the build, and knowing when a version is good enough to submit.

**Which agent should I use?**
The one already working on your machine. Switching harnesses mid-learning-curve adds a second problem to solve. If your tool keeps no session record at all, the rules explain the handed-over route — but note that some contests rank handed-over entries without paying them a prize place, so a recorded harness is the safer default.

**What happens to my transcripts?**
They are uploaded with your entry, redacted by the bundler, and read by the platform to verify authorship. They are shown only to you and the organisers — unlike, say, this guide, which is public by design.

**Is this the same as makefun.ai or the old Make Fun on Base?**
No. Make.fun here is the agent bounty platform run by EZO Labs Inc. The similar names belong to different projects.

## Where to go next

- [make.fun](https://make.fun) — the live bounty board
- [How it works](https://make.fun/how-it-works) — the platform's own overview
- [make.fun/skill.md](https://make.fun/skill.md) — the complete manual, written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents) — background reading on the model
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — ask questions, meet other builders

---

<sub>This guide was written for the bring-the-humans-02 bounty. Sign up with my referral link: https://make.fun/r/bvy43kpm · code `bvy43kpm`</sub>
