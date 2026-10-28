---
type: knowledge
tags:
  - methodology
  - moc
updated: 2026-09-19
related: "[[01 Scaling the foundation]]"
---

# Foundation of project structure

Before this document: if it's unclear how much of the methodology below
needs to be followed right now, it's faster to start with
[[07 Minimum, core and complexity limits]]. Not everything described
here is mandatory from day one.

A symbiotic system of three methodologies: **Johnny.Decimal** (rigid
addressing), **P.A.R.A.** (relevance dynamics), and **MOC / LYT**
(content maps for navigation). All three are reinforced by a fourth
layer — rules that make the structure predictable for an AI agent
reading and editing files.

## 1. Johnny.Decimal — a rigid addressing skeleton

Deeply nested folders are equally hard to read for a human and for an
AI: the more levels there are, the more expensive it is to figure out
where a file lives without reading it. Johnny.Decimal solves this with
numeric prefixes: a category inside a project gets a two-digit number
instead of a meaningful nested tree. Depth shouldn't exceed 2–3 levels
(`Area → Category → file`), or the token cost of scanning the tree grows
and the AI starts losing track of paths.

A practical breakdown of the number pipeline:

- **`00-inbox`** — a raw buffer: chat dumps, briefs, unsorted files. Not
  a storage location — files get sorted out of it into their target
  categories.
- **`10-sources`** — immutable originals (see the "read-only" rule in
  section 4).
- **`15-knowledge`** — cleaned-up atomic notes, the same meaning as
  `(R) Resources` at the top level.
- **`20-questions`** and **`40-experiments`** — active work: open forks
  and whatever's being tested right now in isolation.
- **`30-decisions`** — a fixed choice (ADR), usually the outcome of a
  closed question or a successful experiment.
- **`50-people`** — contributor profiles, areas of responsibility; if a
  file relates to both a person and a decision, the "one file, one
  address" rule (section 2) puts it wherever the defining category is,
  and the other area gets a wikilink.

The practical effect: on seeing the `20-` prefix, both a human and an AI
know the content type instantly without reading it — it's an open
question, not knowledge, not a decision. A new file gets created by
prefix, not "wherever seems logical."

## 2. P.A.R.A. — relevance dynamics

Tiago Forte's method splits information not by topic, but by how needed
it is right now:

- **Projects** — what's actively being worked on, with a goal/horizon.
- **Areas** — zones of ongoing responsibility with no fixed finish line.
- **Resources** — a reference base: knowledge, sources, processes,
  templates.
- **Archives** — everything finished or no longer relevant, but not
  deleted.

In this vault, the top level is P.A.R.A. (`(P) Projects`, `(R)
Resources`, `(A) Areas`/`(A) Journal`, `(a) Archive`), and
Johnny.Decimal works **inside** each project or resource section as a
second addressing layer. One file, one physical address; if it relates
to two areas, the second area gets a wikilink, not a copy.

## 3. MOC / LYT — content maps and navigation

Inside a project or section, dispatcher files are set up that store
nothing themselves, only collect links and live queries
(Dataview/Tasks): `README.md` (entry point), `state.md` (dashboard),
`plan.md` (current horizon), `journal.md` (append-only log). Both the AI
and the human start orienting themselves from the map, not by scanning
the whole folder — this sharply cuts the token cost of every request.

## 4. The layer for the AI agent

Strict addressing is valuable precisely because it takes "where does
this go" off the AI's plate — the structure already answers it. The
technical layer (`_access`, `_env` — access scripts and environment
config) is kept separate from user content on the same principle:
secrets and system keys don't get mixed in with notes, so they're easier
to exclude from indexing and from commits. Concrete rules follow from
this:

- **Frontmatter is the file's passport.** Every file opens with a YAML
  block. Field keys are in Latin/English (`status`, `priority` — or an
  established project-specific alias, if that's been decided for the
  project), values are plain language. Consistency of keys matters more
  than their spelling: what matters is that one project doesn't mix two
  spellings of the same field without a reason. The list of values
  already in use is in [[02 Tags, types and statuses]].
- **Typed entities carry an `id`.** A question is `Q-NN`, a decision is
  `D-NN`, a process is `P-NN`, an experiment is `E-NN`. The number is
  sequential within its type and never reused, even after closing.
- **Every question has a mandatory "What changes with the answer"
  section.** If the answer changes nothing, it's not a question — the
  file shouldn't exist.
- **Every decision has "Rationale" and "Rejected alternatives."** The AI
  doesn't make decisions for the human: it files decisions with status
  `proposed`, and moving to `accepted` is a human action.
- **Sources (`10-sources`) are read-only.** An error in a source is a
  fact about the source, not a reason to fix it — it gets recorded in a
  knowledge note instead.
- **A secret never goes into a file.** Not in a new one, not in an old
  one, not in a sample config — not even partially, not even "just the
  variable name" if the variable itself is the secret.
- **Edit the block, not the whole file.** When updating `plan.md` or
  `state.md`, change the specific section — everything else, including
  the human's own comments, stays as it was.
- **The journal only grows downward.** Lines are never edited or
  deleted; a mistake gets fixed with a new line, not a correction to the
  old one. After a notable step (a new feature, a structural change, a
  closed question), a journal entry isn't optional — it's part of the
  action: without it, the step didn't happen as far as anyone else is
  concerned.
- **The human gets their own entry points.** A human doesn't create
  files directly at an arbitrary point in the structure: a new idea, bug,
  or brief lands in `00-inbox` or gets written up directly as
  `20-questions`; sorting into Johnny.Decimal categories is the AI's
  job, not the human's.
- **File authorship is explicit.** A file created or rewritten by the AI
  can be flagged in frontmatter with a separate value (for example a
  tag/status "AI-generated") until a human has reviewed and taken
  ownership of the content. This doesn't block edits — it just records
  who's currently responsible for the file being correct.

## 5. What this adds up to

Johnny.Decimal gives the structure a skeleton (predictable addresses),
P.A.R.A. gives it dynamics (what matters right now), MOC gives it
navigation (maps instead of scanning), and the AI rules give it a
language the agent can use to read and extend the vault without
damaging existing content. A working example is the folder
[[01 Example of a mature project/README|JDPARA-EN/(P) Projects/01 Example of a mature project]]
in this same kit.

Next: [[01 Scaling the foundation]] — carrying the scheme across several
projects at once and multi-agent scenarios; [[05 Project lifecycle]] —
how a single project uses this structure over time, from birth to
archive.
