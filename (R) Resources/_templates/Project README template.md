---
type: project
status: concept
priority: 2
updated: YYYY-MM-DD
tags: [project]
---

# {{Project name}}

One or two paragraphs: what this is, who it's for, why it exists. No
retelling of the folder structure — that's the "Structure" section
below.

## A new session starts here

1. [[state]] — what's already done, what's confirmed
2. [[plan]] — the current horizon
3. [[journal]] — timeline

## Structure

```
README.md          ← this file
CLAUDE.md           ← rules of work for the AI agent
state.md            ← dashboard: what's known right now
plan.md             ← current horizon, no checkboxes
journal.md          ← append-only log
00-inbox/           ← raw, unsorted
10-sources/         ← immutable originals, read-only
15-knowledge/       ← atomic, cleaned-up notes
20-questions/       ← open forks, prefix Q-
30-decisions/       ← fixed choices with rationale, prefix D-
```

## Rules of work

Full rules are in this project's [[CLAUDE]]. Key points:

1. Every step gets a line in [[journal]], new ones at the bottom.
2. Sources aren't edited — an error in a source gets recorded in
   knowledge, not fixed in place.
3. A question with no "what changes with the answer" section doesn't get
   created.
4. Secrets never go into files in this vault.
