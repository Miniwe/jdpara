---
type: knowledge
tags:
  - methodology
  - moc
updated: 2026-09-19
related: "[[00 Foundation of project structure]]"
---

# Minimum, core and complexity limits

This kit already has six documents, which creates a risk that's the
opposite of the system's own goal: a methodology invented to take the
"where does this file go" burden off a person turns into something that
has to be learned before it can be used at all. This document isn't a
new rule — it's a map of how much of what's already described actually
needs to be known **right now**, and at what level to stop.

Read by level: each next level is optional if the previous one is enough
for the task at hand. Reading all of it once is fine — working by all of
it at once is not necessary.

## Level 0 — if this is a one-off note

Not everything needs Johnny.Decimal, MOC files, and statuses. If the
task is one note, one to-do list, a one-off thought with no forks —
just write the file. [[(P) Projects/02 Example of a simple
project/README|02 Example of a simple project]] is exactly that case:
`README.md` and `Tasks.md`, no `20-questions`, no `state.md`, not a
single term from [[02 Tags, types and statuses]]. The sign that level 0
is enough: there's no fork in the task worth remembering a month from
now.

## Level 1 — the minimum for keeping it simple

As soon as there's more than one note and connections start forming
between them — a minimal but deliberate set kicks in:

1. **One physical address per file.** The rule from section 2 in
   [[00 Foundation of project structure]] — the one thing without which
   the structure collapses immediately: if a file lives in two places,
   any map about it is lying. This isn't Johnny.Decimal or PARA — just
   discipline.
2. **Frontmatter with `type` and `status`.** Not the whole
   [[02 Tags, types and statuses]] reference — just these two fields,
   and only the values actually needed right now. The other types in the
   reference don't need to be set up ahead of time "for later."
3. **A README as the entry point.** One door-note per project/section —
   not a MOC with Dataview queries, just a file where orientation
   begins.

This is enough for most personal projects. Everything [[00 Foundation of
project structure]] describes beyond this list (the `00-`…`50-` numbers,
the full set of AI-agent rules) is level 2, not required to get started.

## Level 2 — the full methodology core

This is where the entire content of [[00 Foundation of project
structure]] kicks in: Johnny.Decimal with numeric prefixes, typed
entities (`Q-NN`, `D-NN`) with their own statuses ([[02 Tags, types and
statuses]]), MOC files (`plan.md`, `state.md`, `journal.md`) as live
maps, and the AI-agent rules (frontmatter as a passport, no overwriting a
block, journal only growing downward).

The signal that it's time to move here isn't "the system looks
impressive" — it's specifically one of three things:

- the project has more than one open fork that needs to be remembered
  past a single session — `20-questions` gets started;
- the project has gone through a decision someone will later come back
  to ask "why was it done this way" — `30-decisions` gets started;
- an AI agent works on the project regularly, and without a map
  (`state.md`) every run starts by scanning the whole folder.

If none of the three signals has fired — level 1 isn't "incomplete," it's
sufficient, and moving to level 2 would add more files to maintain than
problems it solves. [[05 Project lifecycle]] separately notes that the
move doesn't have to be instant or complete — MOC files can be added one
at a time, when the signal appears, rather than all at once.

## Level 3 — scale and multi-agency

Everything from [[01 Scaling the foundation]]: top-level aggregators
([[Focus]], [[Task summary]]) across several projects, dividing roles
among several AI agents, the `assigned_to` protocol for handing off file
ownership, and [[06 Vault hygiene and review]] as a regular check-in
procedure.

This level is only needed if one of two conditions holds: more projects
are active at once than fit in a head without an aggregator
(practically, more than 3–4), or more than one AI agent works on the
vault in parallel. If it's one person with one assistant on one or two
projects — level 3 isn't needed at all, and trying to set up a
file-locking protocol or agent roles ahead of time is complexity with no
problem to solve.

## Diagnosis: the system has become a burden, not a help

Signs it's time to stop or roll back a level, rather than add one more
rule:

- **Editing frontmatter instead of doing the task.** If picking the
  right `type`/`status` from the reference takes longer than the task
  itself — the reference is getting in the way at that moment, not
  helping. The fix isn't to memorize the reference more thoroughly, but
  to use a simplified value and add it to [[02 Tags, types and
  statuses]] afterward, rather than hunting for the perfect one now.
- **Cards get created out of discipline, not necessity.** The rule
  "every question needs a mandatory 'What changes with the answer'
  section" (section 4 in [[00 Foundation of project structure]]) exists
  precisely for this symptom: if the answer changes nothing, it's not a
  question, and wrapping a `Q-NN` around the thought is form without
  function.
- **A MOC file exists, but nobody looks at it.** A map no one opens
  before working doesn't do its job (section 3 in [[00 Foundation of
  project structure]]) — if `state.md` consistently goes stale and that
  doesn't get in the way of the work, it's a signal the project never
  actually needed level 2 for that part, not that the MOC isn't being
  maintained diligently enough.
- **The review from [[06 Vault hygiene and review]] finds more problems
  than it saves time.** If reviewing the vault itself turns into a
  multi-hour task, that's a symptom the structure outgrew the actual
  project volume, not that reviews need to happen more often.
- **Onboarding a new contributor takes longer than the work itself.** If
  someone joining the project has to read every document in this kit
  before making their first useful edit — that's a reason to cut the
  rule set for that specific project down to level 1, rather than ask
  them to read faster.

The general diagnostic rule: the system should remove the question "how
do I do this" and leave only "what do I do." The moment it starts
answering "what's the proper way to format this" — a question that
didn't exist before the system showed up — it has exceeded the level the
task actually needs.

## The complexity growth curve

Complexity doesn't grow linearly with the number of projects — it jumps
at the level boundaries above. Within one level, adding another project
or another note barely adds load (the structure already exists, the
file just takes its place). The cost is paid at the moment of
transition: setting up the first `CLAUDE.md`, the first `assigned_to`
protocol, the first review process — each such transition deserves
attention, not automatic repetition.

The practical takeaway: don't design the structure ahead of time for the
maximum level "just in case." It's cheaper to stay at level 1 longer
than strictly necessary and move to level 2 on a concrete signal, than
to roll out the whole core at once and maintain documents that have no
job yet. Symmetrically: if level 2 or 3 signals are already recurring,
delaying the move doesn't save complexity — it just accumulates
invisibly (in someone's head, not in the structure), and sooner or later
shows up as one of the problems in the diagnosis section above.

## How to read the rest of this kit's documents

The takeaway for the whole set isn't "read everything" — it's knowing
where to come back to on a signal:

| Document | When to open it |
|---|---|
| [[00 Foundation of project structure]] | moving to level 2 — need the full methodology vocabulary |
| [[01 Scaling the foundation]] | moving to level 3 — several projects or agents |
| [[02 Tags, types and statuses]] | as a reference for a specific value, not to read end to end |
| [[03 Obsidian setup]] | once, when setting up the tool — unrelated to the methodology level |
| [[05 Project lifecycle]] | when a project changes stage (priority, closing) |
| [[06 Vault hygiene and review]] | once level 3 is already adopted and a review rhythm is needed |

This document isn't a step between them, it's a filter in front of all
of them: if it's unclear which of the six to open, start here and follow
the level, not the numbering order.
