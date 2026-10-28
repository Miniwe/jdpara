---
type: knowledge
tags: [moc]
related: "[[(R) Resources/00 Foundation of project structure]]"
---

# Structure of this kit

A one-page map. Full rationale is in
[[(R) Resources/00 Foundation of project structure|Foundation of project structure]].

## Root

| File | Role |
|---|---|
| [[Focus]] | which projects are currently in focus and what matters most there — reads project frontmatter |
| [[Task summary]] | a counter of open tasks across all projects |
| [[Kanban board]] | a manual top-level board — a no-thought entry point, not for projects |

## (P) Projects

PARA: Projects. Each project is a folder with its own README and
(optionally) a CLAUDE.md. Inside a project, Johnny.Decimal prefixes mark
content types: `00-inbox`, `10-sources`, `20-questions`, `30-decisions`.
Not every project has to use every prefix — see the difference between
[[(P) Projects/01 Example of a mature project/README|01 Example of a mature project]]
(full set) and [[(P) Projects/02 Example of a simple project/README|02 Example of a simple project]]
(just a README + a flat task list).

## (R) Resources

PARA: Resources. Methodology and templates not tied to any specific
project. `_templates/` holds drafts for a README, a CLAUDE file, a
question, a decision: copied into a project and filled in.

## (A) Areas

PARA: Areas. The same pipeline as inside a project (inbox → idea →
question → decision → experiment), but for things not tied to a single
goal with a horizon — an area of ongoing responsibility with no finish
line. See the [[(A) Areas/README|README]] of this folder.

## (A) Journal

One file per day (`YYYY-MM-DD.md`), three zones: focus of the day,
checklists, incoming log. Gets processed into `(A) Areas`/`(P) Projects`
as it accumulates; the day file itself moves to `(a) Archive/Journal`
once a calendar threshold is reached, not right after it's processed.

## (a) Archive

PARA: Archives. Mirrors `P/R/A`, but flat. This is where finished work
**moves** (not copies) to: whole projects, closed questions, completed
experiments, old journal days. See the [[(a) Archive/README|README]] of
this folder.

## (R) Utility

Technical infrastructure — outside the P.A.R.A. loop, not part of the
knowledge pipeline: attachments, audio, Copilot's own data, rhythm
templates (day/week). See the [[(R) Utility/README|README]] of this
folder.

## The direction of flow

Raw (`00-inbox`) → understood (`20-questions`, discussion) → fixed
(`30-decisions`, `15-knowledge`). There's no flow backwards — revisiting
a decision means a new decision that links to the old one, not editing
the old one.
