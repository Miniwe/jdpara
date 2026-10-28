---
type: knowledge
tags:
  - methodology
  - moc
updated: 2026-09-19
related: "[[00 Foundation of project structure]]"
---

# Project lifecycle

[[00 Foundation of project structure]] describes the static skeleton of
a single project, [[01 Scaling the foundation]] describes how several
such projects and agents live side by side. Here — the third dimension:
what happens to **one** project along the axis of time, from first idea
to archive, and at what point each already-described rule kicks in.

## 1. Birth: from idea to README

A project doesn't appear "complete" right away — with a polished README,
a CLAUDE.md, and a full Johnny.Decimal structure. The entry-point rule
(section 4 in [[00 Foundation of project structure]]) applies to the
project itself too: an idea first lands in the general-level `00-inbox`
or gets written up as `20-questions` — "is this worth being its own
project" — and only then turns into a `(P) Projects` folder.

The minimal skeleton of a new project:

1. A `README.md` from [[Project README template]] — an entry card: what
   it is, why it exists, `priority` (see [[02 Tags, types and
   statuses]]).
2. A `CLAUDE.md` from [[Project CLAUDE template]] — if the project needs
   its own rules for the AI beyond the general ones (section 4 in
   [[00 Foundation of project structure]]).
3. Only the Johnny.Decimal categories actually needed right now.
   [[(P) Projects/02 Example of a simple project/README|02 Example of a
   simple project]] gets by without `20-questions`/`30-decisions` at all
   — the full set from [[(P) Projects/01 Example of a mature
   project/README|01 Example of a mature project]] isn't mandatory from
   day one.

A project doesn't have to be born at `priority: 1` — a card can be
started in advance (`priority: 3`, background) and filled in slowly.

## 2. Growth: when to set up MOC files

The `plan.md`, `state.md`, `journal.md` files (section 3 in
[[00 Foundation of project structure]]) aren't mandatory from day one —
their cost is justified once scanning the folder is already more
expensive than reading the map. A practical signal: as soon as a project
has more than one open card (`20-questions` or `30-decisions`), or the
work spans more than one session, the MOC files pay for themselves.

The reverse signal — if a project stays a simple task list with no
question cards (like [[(P) Projects/02 Example of a simple
project/README|02 Example of a simple project]]), the full MOC set isn't
needed: a `README.md` and a `Tasks.md` are enough, and adding `state.md`
just for the sake of form is one more file no one will keep updated.

## 3. Changing priority: a decision, not a technical action

The `priority: 3 → 2 → 1` transition isn't a single-field edit, it's a
signal that top-level aggregators react to ([[Focus]], [[Task summary]],
the "Several projects at once" section in [[01 Scaling the
foundation]]). It follows that:

- Lowering priority doesn't have to come with closing open
  `20-questions` — a question can wait alongside the project. An explicit
  `stale` (see [[02 Tags, types and statuses]]) only gets set when the
  question's context has actually disappeared, not automatically when
  the project's priority drops.
- Raising a project to `priority: 1` is the moment to check `state.md`:
  if the MOC files weren't set up back at step 2, now's the time, rather
  than starting active work with no map.

## 4. Completion: closing, not zeroing out

A project closes when its goal is met or dropped — but closing a project
doesn't mean retroactively closing every card inside it. The distinction
matters:

- **What gets fixed before moving.** Open `20-questions` get a real
  status — `answered` if the answer was effectively found along the way,
  `dismissed` if it stopped mattering, or `stale` if its context
  disappeared along with the project. Leaving questions marked `open`
  during archiving creates a false impression that work is continuing.
- **What stays as is.** `30-decisions` aren't rewritten into past tense
  or given a new status just because of archiving — a decision is either
  still in effect (`accepted`) or was already withdrawn during the work
  (`revoked`/`superseded`); archiving itself doesn't change that.
- **The journal gets a final line.** The "journal only grows downward"
  rule (section 4 in [[00 Foundation of project structure]]) applies to
  closing too: the last entry in `journal.md` records the fact and date
  of closing, rather than the project silently disappearing from
  `(P) Projects`.

## 5. Moving to the archive: what happens physically

`(P) Projects → (a) Archive` is not deletion and not compression into a
single file, but moving the same Johnny.Decimal folder as a whole, with
its internal addresses preserved (the "one file, one address" rule,
section 2 in [[00 Foundation of project structure]]). Two consequences
follow:

- **Wikilinks don't break automatically.** If files in the project were
  linked from `50-people` or from the shared `(R) Resources`, moving the
  folder doesn't require editing those links — Obsidian updates them on
  move (see the "Automatically update links" setting in [[03 Obsidian
  setup]]) — but it's worth double-checking external aggregators
  ([[Focus]], [[Task summary]]): they usually filter by
  `priority`/`status`, and an archived project should naturally drop out
  of them rather than linger as an "empty" row.
- **The archive isn't a trash bin.** `(a) Archive` holds finished work
  that might still be needed (section 2 in [[00 Foundation of project
  structure]]), not what's been decided to throw away. If a project
  turned out to be a dead end with no value even as a reference — that
  calls for an explicit decision (`D-NN` with status `revoked`) about
  what's being deleted, not a quiet move into the archive.

## Summary

The same project uses a different part of the methodology from
[[00 Foundation of project structure]] at different times: a minimum at
the start, MOC files as it grows, closing-status discipline at
completion. This isn't a separate methodology layered on top — it's a
map of when each already-described rule applies; the structure itself
doesn't change over the project's lifetime.
