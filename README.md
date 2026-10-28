---
type: readme
icon: package
tags: [moc/inbox]
---

# 📦 JDPARA

A self-contained example vault built on the methodology from
[[(R) Resources/00 Foundation of project structure|Foundation of project structure]]
(Johnny.Decimal + P.A.R.A. + MOC, with rules for an AI agent). Everything
inside this folder is **test data**: demo projects, demo questions, demo
journal days. Nothing from an actual working vault was copied in here.

## How to use it

**Option A — as a reference inside your current vault.** Leave the
folder here and open files through normal Obsidian navigation — every
wikilink inside `JDPARA-EN` is self-contained within the folder
and resolves correctly regardless of the rest of the vault.

**Option B — as a standalone vault, handed to someone else.** Copy the
whole `JDPARA-EN` folder and open it in Obsidian as a new vault
(`Open folder as vault`, pointing at `JDPARA-EN` itself, not its
parent). Every path inside is relative to this folder, so it carries no
dependencies on the rest of `LifeTracker`.

## What's inside

```
README.md                          ← this file
structure.md                       ← a short map of how it's organized (read second)
Focus.md                           ← live dashboard "what's in focus / what matters" (test data)
Task summary.md                    ← live aggregator of open tasks (test data)
Kanban board.md                    ← manual top-level board (test data)
(P) Projects/
  01 Example of a mature project/  ← full profile: README, CLAUDE, questions, decisions, sources
  02 Example of a simple project/  ← minimal profile: README + flat task list
(R) Resources/
  00 Foundation of project structure.md   ← the methodology all of this is built on
  01 Scaling the foundation.md            ← scaling to several projects and to AI agents
  02 Tags, types and statuses.md          ← reference of allowed frontmatter values
  03 Obsidian setup.md                    ← plugins and settings — how to recreate the environment from scratch
  _templates/                             ← templates for README/CLAUDE/question/decision
(A) Areas/                         ← PARA: Areas — a pipeline outside the scope of any single project
  00 Inbox/, 10 Ideas/, 20 Questions/, 30 Decisions/, 40 Experiments/
(A) Journal/
  2026-09-19.md                     ← example day
(a) Archive/                       ← PARA: Archives — where finished work moves
  Projects/, Questions/, Experiments/, Journal/
(R) Utility/                       ← technical infrastructure, outside P.A.R.A.
  Assets/, Audio/, copilot/, Templates/
```

## Where to start reading

1. [[structure]] — a one-page map
2. [[(R) Resources/00 Foundation of project structure|Foundation of project structure]] — why the structure looks the way it does
3. [[(P) Projects/01 Example of a mature project/README|Example of a mature project]] — what it looks like in practice
4. [[Focus]] and [[Task summary]] — how dashboards read projects automatically
5. [[(A) Areas/README|(A) Areas]] — the same pipeline (idea → question → decision), but outside the scope of a single project
6. [[(a) Archive/README|(a) Archive]] — where and when finished work gets moved
7. [[(R) Utility/README|(R) Utility]] — the purpose of Assets/Audio/copilot/Templates and related settings

## Frontmatter convention

Field keys are in Latin/English (`status`, `priority`, `id`); values are
plain language. A project can also settle on its own alias for a key, as
long as it's used consistently — what matters is not mixing two
spellings of the same field inside one project.
