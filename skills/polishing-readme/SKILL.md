---
name: polishing-readme
description: Use when a repository's README is missing, thin, outdated, or hard to scan, when the user asks to "clean up the README", "document this", "make it look professional", or before publishing a package, plugin, or template
---

# Polishing a README

## Overview
A README has one job: get a stranger from "what is this?" to a working first run in under two minutes. Everything else goes below the fold or into docs/.

## Step 1: Audit against the repo, not the old README
Check what the code actually does today: entry points, CLI flags (`--help`), config files, package manifest, tests, CI badges that are real. Old READMEs lie; code does not.
List every claim in the current README that the code no longer supports, and remove them.

## Step 2: Write the above-the-fold block
In this order, with no other sections between them:
1. **Name + one-line outcome** (the verb phrase, not the category)
2. **Install**: one copy-pasteable command per supported method. One prerequisite line above the commands if a toolchain is assumed. Only commands you have run or found in the project's own docs; otherwise write `[[VERIFY: command]]`.
3. **First run**: the smallest command that produces visible output, plus that output. For a project with no command (library, skill, plugin, template): the smallest usage (an import, a prompt, a file) and what it produces, labeled as an example.
4. **Proof**: real badges only (CI, version, license). If none exist, one plain line: `Version X.Y.Z · License`. Screenshot or GIF if the tool is visual.

## Step 3: Below the fold, in this order
| Section | Include when |
|---|---|
| Usage | More than one command or flag. Use a table for flags. |
| Configuration | A config file or env vars exist. Show a complete minimal example. |
| Pricing / tiers | A paid tier exists. One table, same rows for every tier. |
| How it works | A non-obvious mechanism (caching, parsing, auth) affects behavior. 150 words or fewer. |
| Troubleshooting | Any error users will hit. Error text verbatim when one exists, otherwise the symptom in the user's words, then the fix. |
| Contributing | The repo is public with issues or PRs enabled, or the user says contributions are wanted. Link to CONTRIBUTING.md if long. |
| License | Always. One line. |

Skip sections with nothing to say. Never leave a heading with placeholder text.

## Step 4: CHANGELOG.md
If absent, create one in Keep a Changelog form with an `Unreleased` section and the current version taken from the manifest or latest tag. For a first release with no tags, list what that version ships under `Added`, one line per capability. If present, verify the top entry matches the manifest version.

## Example (above the fold)
````markdown
# relnotes

Turn your git log into a changelog people actually read.

```bash
npm install -g relnotes
```

```bash
$ relnotes --since v1.2.0
## v1.3.0 (2026-05-02)
### Added
- OAuth login (#142)
### Fixed
- Crash on empty commit body (#150)
```

[![CI](https://github.com/org/relnotes/actions/workflows/ci.yml/badge.svg)](https://github.com/org/relnotes/actions) ![npm](https://img.shields.io/npm/v/relnotes) MIT
````

## Common mistakes
- Opening with a paragraph of history or motivation. Move it to "How it works" or delete it.
- Install instructions that assume a toolchain the reader may lack. State the prerequisite once.
- A "Features" bullet list instead of a first run. Show output and let the reader infer features.
- Badges for services the repo does not use. Remove them.
- Table of contents on a README under 150 lines. Remove it.
