---
name: writing-launch-copy
description: Use when a project needs a landing page, store listing (Gumroad, Chrome Web Store, npm, marketplace), Product Hunt post, or Show HN text, or when the user asks "how do I describe this", "write the pitch", or "make a landing page for this"
---

# Writing Launch Copy

## Overview
Launch copy sells an outcome, not a feature list. Every block below answers one buyer question, in the order a buyer asks it.

## Step 1: Extract the facts (never invent them)
Read the repo before writing anything. Sources in order: README, manifest (package.json, plugin.json, pyproject), entry files and `--help`, tests, scripts, git log. Use whichever exist; an empty repo still has a manifest or a file tree.
- What it does in one verb phrase (`turns git log into release notes`)
- Who has the problem (role + situation, e.g. "solo devs shipping weekly")
- The painful alternative today (manual, slow, expensive, error-prone; pick the real one)
- 3 to 5 concrete capabilities with proof (file, command, screenshot, number)
- Install / buy / try command or link
- Price and license (ask if missing; do not guess)

If a fact is missing, write `[[ASK: price?]]` in the draft instead of inventing. A link that does not exist yet is `[[ASK: url?]]`. An undecided product name is `BRAND`.

## Step 2: Fill the copy contract
Produce exactly these blocks, in order. Headings are for you; the user may drop them.

| Block | Rule |
|---|---|
| Headline | 10 words or fewer. Outcome + audience. Product name optional. |
| Subhead | One sentence: what it is + the alternative it replaces. |
| Proof bar | 1 to 3 verifiable facts about adoption or construction (stars, users, "0 dependencies", "works offline", license). Terms such as refund or price belong in the CTA. Omit if none; never fake. |
| Problem | 2 to 3 sentences describing the buyer's situation. Name the Tuesday-afternoon pain. No invented quotes. |
| Capabilities | 3 to 5 bullets, one line each. Each: **bold outcome**, then how, with a concrete noun. Group related features into one bullet rather than listing every one. |
| How it works | 3 numbered steps, each 12 words or fewer, each starting with a verb. |
| Call to action | Command or button text + price + risk reverser (refund, free tier, MIT). |
| FAQ | 3 to 5 questions buyers actually ask: compatibility, privacy, updates, refunds. |

## Step 3: Channel variants
After the master copy, emit per-channel cuts on request:
- **Gumroad / store listing**: Headline, Subhead, Capabilities, FAQ. Plain text: no HTML, no Markdown. The bold outcome becomes the bullet's first sentence.
- **Product Hunt**: tagline 60 chars or fewer; first comment (150 words or fewer, first person) = Problem + How it works + what you want feedback on.
- **Show HN**: title `Show HN: <name> – <outcome>`; body 250 words or fewer, first person, plain: Problem (2 sentences), how it works, one line with price and install, Limitations (3 to 5 honest bullets from the repo's gaps), one specific feedback request. No marketing adjectives.
- **README hero**: Headline + Subhead + install command only.

## Example (master copy, abridged)
```
Headline: Release notes from your git log, in one command
Subhead: A CLI that turns commits into a changelog people actually read. No more Friday copy-paste.
Capabilities:
- **Ships a changelog in 4 seconds**: reads conventional commits, groups by type, links PRs.
- **Zero config**: works on any repo with `npx relnotes`.
- **Markdown or GitHub Release**: `--gh` publishes directly.
CTA: `npx relnotes` · Free for public repos · Pro $9 one-time, 30-day refund
```

## Common mistakes
- Headline names the product instead of the outcome. Rewrite with the verb.
- "Powerful", "seamless", "blazing fast". Replace with a number or a noun.
- Capabilities that are features ("supports YAML"). Add the outcome ("so config lives in git").
- Inventing user counts or testimonials. Use `[[ASK]]` markers and leave the proof bar out.
