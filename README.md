# Launch Kit for Claude Code

Take a side project from working code to a shipped, sellable product: six Claude Code skills for launch copy, SEO articles, README polish, release notes, pricing pages, and a pre-launch checklist.

## Install

Prerequisite: [Claude Code](https://claude.com/claude-code) installed.

**Free tier** (two skills, MIT) - copy the skill folders into your skills directory:

```bash
git clone https://github.com/sidelabhq/launch-kit.git
cp -r launch-kit/skills/writing-launch-copy launch-kit/skills/polishing-readme ~/.claude/skills/
```

Or load the cloned folder as a plugin for one session:

```bash
claude --plugin-dir ./launch-kit
```

**Pro tier** (all six skills, $12 one-time) - buy at [sidelabhq.gumroad.com/l/launch-kit](https://sidelabhq.gumroad.com/l/launch-kit), unzip, then copy every skill folder:

```bash
unzip launch-kit-pro-1.0.0.zip -d launch-kit-pro
cp -r launch-kit-pro/skills/* ~/.claude/skills/
```

Claude Code watches the skills directory and picks up new skills in the current session. If `~/.claude/skills/` did not exist when your session started, run `/reload-skills` once.

## First run

Inside a repository that has no README:

```
> polish the README

I'll start by auditing the repo: manifest, entry points, license, and
any CI config, then write the above-the-fold block.

  Wrote README.md (Name, Install, First run, Usage, License)
  Created CHANGELOG.md (Unreleased + 1.0.0 from package manifest)
```

The skill triggers on its own when your request matches its description, or you can ask for it by name ("use the polishing-readme skill").

Version 1.0.0 · Free tier: MIT

## Usage

Each skill fires when the request matches its description, or when you name it.

| Skill | Tier | Triggers on | Produces |
|---|---|---|---|
| `writing-launch-copy` | Free | "write the pitch", "make a landing page for this", a Gumroad / Product Hunt / Show HN listing | Headline, subhead, proof bar, problem, capabilities, how it works, CTA, FAQ; per-channel cuts on request |
| `polishing-readme` | Free | "clean up the README", "document this", "make it look professional", before publishing | A README with install, first run, and proof above the fold; `CHANGELOG.md` if missing |
| `writing-seo-articles` | Pro | "an article about X", "a how-to", "content for the blog", or a keyword to rank for | Intent line, outline, draft with runnable proof, slug / meta description / tags block |
| `writing-release-notes` | Pro | "what changed since", "write the release notes", tagging a release, updating `CHANGELOG.md` | Versioned notes from the git diff since the last tag, prepended to `CHANGELOG.md`, plus a GitHub Release body and a store "What's new" line |
| `writing-pricing-pages` | Pro | "how much should I charge", "free vs pro", "what goes in the paid tier" | A pricing model with reasoning, the free/paid line, tier cards, risk reversers, and FAQ |
| `running-launch-checklist` | Pro | "ready to ship", "let's launch", "is this ready", before a first public release | A 15-item PASS / FAIL / ACCEPTED table with evidence and a READY / NOT READY verdict |

Skills that need facts they cannot find in the repo (price, user counts, testimonials) write `[[ASK: ...]]` markers instead of inventing them. Grep for `[[ASK` before publishing.

## Free vs Pro

| | Free | Pro |
|---|---|---|
| Price | $0 | $12 one-time, on [Gumroad](https://sidelabhq.gumroad.com/l/launch-kit) |
| Skills | `writing-launch-copy`, `polishing-readme` | All six |
| License | MIT | Personal and commercial use on all your own machines; no redistribution |
| Updates | This repository | Lifetime updates included |
| Refund | - | 30 days, on request |

## How it works

A skill is a folder containing a `SKILL.md` with a YAML `name` and `description` plus the instructions Claude follows. Claude Code reads every folder under `~/.claude/skills/` (or a loaded plugin's `skills/`) and watches it for changes, so a newly copied skill is available in the current session. During a session the description is matched against your request; when it fits, the skill's instructions are loaded and followed. Nothing runs in the background and no network calls are made by the skills themselves. The six skills cross-reference each other (the launch checklist, for example, checks that the README, release notes, and pricing exist), but each works alone.

## Troubleshooting

**The skill did not trigger.** Run `/reload-skills` (needed once when the skills directory was created after the session started). If it still does not fire, ask for it by name ("use the writing-launch-copy skill") and check that the folder in `~/.claude/skills/` still contains `SKILL.md` with its frontmatter intact.

**Copy contains `[[ASK: ...]]`.** The skill could not find that fact in the repo. Answer it in chat and ask Claude to fill the marker; never ship copy with a marker left in.

## Contributing

Issues and pull requests for the two free skills are welcome in this repository. The Pro skills are not redistributable; send Pro feedback through the Gumroad purchase page.

## License

Free tier (`writing-launch-copy`, `polishing-readme`): MIT. Pro tier: licensed to the purchaser, see [LICENSE](LICENSE).
