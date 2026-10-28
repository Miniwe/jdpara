---
type: knowledge
tags:
  - methodology
  - moc
updated: 2026-09-19
related: "[[00 Foundation of project structure]]"
---

# Scaling the foundation

Starting point: [[00 Foundation of project structure]]. Here — how the
scheme behaves once there are many projects and/or several AI agents are
working at the same time.

## Several projects at once

Nothing changes in the structure of a single project — what changes is
what reads **all of them at once**. The top-level files (`Focus.md`,
`Task summary.md`) store no data themselves; they build a live query
(Dataview/Tasks) on top of each project's frontmatter:

- `priority` (1 — in focus, 2 — relevant, 3 — background) in each
  project's `README.md` answers "what's even being worked on."
- Open questions (`20-questions/Q-*.md`) with a priority/status field
  answer "what matters most inside this project right now."

A single aggregator shouldn't decide a project's priorities for it — it
only reads what the project has already declared in its own
frontmatter. If the field schema differs between projects (one has
`priority`, another only has `status`) — the aggregator adapts to both,
rather than forcing projects onto a single format for the dashboard's
sake.

## Scaling to multi-agent scenarios

If several AI agents work on the same vault in parallel, the structure
turns into a shared blackboard: Johnny.Decimal's predictable addresses
let agents work asynchronously, each in its own zone (least-privilege
principle), without needing to negotiate where things go — that's
already decided by the folder prefix.

A practical role layout on top of this structure:

| Agent role | Read access | Write access |
|---|---|---|
| Triage | `00-inbox` | all folders — sorts by type |
| Analyst/architect | `10-sources`, `15-knowledge` | `30-decisions` (with status `proposed`) |
| Executor | `30-decisions` | `40-experiments` |
| Supervisor/navigator | the whole vault | only MOC files (`plan`, `state`, `journal`) |

System prompts for each role live not in a human's head or in chat, but
as files: `.claude/agents/` holds one Markdown file per role
(frontmatter with available tools, body as the system prompt). This is a
native Claude Code mechanism, not a custom layer — real projects
(Arkhitsyn, GoalScorer) are already built this way. A role stays
reproducible across session restarts and doesn't depend on who happened
to phrase it.

## Locking protocol: who currently owns a file

Splitting roles across folders removes the "where do I write" conflict,
but not the "two agents reading the same file as a instruction to act on
at the same time" conflict. For entities that pass through several
roles in sequence (question → decision → experiment), two fields get
added to frontmatter on top of the base set (section 4 in
[[00 Foundation of project structure]]):

```yaml
assigned_to: "Architect-Agent"   # current owner, has write rights
last_updated_by: "Triage-Agent"  # who made the last edit
```

Rule: an agent can **read** any file, but may only **write** to it or
treat it as instructions to act on if `assigned_to` names that agent, or
the file sits in its "home" folder by Johnny.Decimal and hasn't yet been
handed further down the pipeline. Transferring ownership means changing
the value of `assigned_to`, not silently taking over the file.

## Risks this scheme doesn't solve on its own

- **Simultaneous writes to one file.** Plain text files don't support
  locking — two agents (or an agent and a human) writing to `plan.md` at
  the same time can overwrite each other or end up with a duplicate file
  from sync. Mitigation: edit the block, not the whole file (section 4
  in [[00 Foundation of project structure]]), the `assigned_to` protocol
  above, and one active session per MOC file. This doesn't fully
  eliminate the race — at high concurrency you need an external write
  queue broker, not just a frontmatter convention.
- **Token cost of constant scanning.** The more notes there are, the
  more expensive it is for an agent to hold context: every touch of the
  vault is text in the context window, and as the base grows to hundreds
  of files, a routine pass over `00-inbox` becomes a real line item.
  MOC files exist precisely so an agent opens the map instead of the
  whole folder — if the agent reads everything regardless, the MOC isn't
  doing its job. As the vault keeps growing, the next step isn't "read
  the MOC" but not reading whole files at all: vector search (RAG) over
  the vault, surfacing only relevant paragraphs.
- **Agent addressing mistakes.** Even a disciplined agent will sometimes
  file a decision under `40-experiments` instead of `30-decisions`,
  break the frontmatter (an unclosed YAML quote), or mix up a
  neighboring prefix (`11-` instead of `10-`). This isn't a reason to
  abandon the structure — it's a reason to check against the map
  (`state.md`) after every session rather than trust it blindly. If the
  same mistake keeps recurring, the fix is not another rule in the
  prompt but an external linter that checks structure and frontmatter
  before anything is actually written to disk, and blocks the save on a
  violation.
- **Rule drift as the team/project count grows.** Rules that live in one
  person's head don't automatically scale to several people or a dozen
  projects: people mix up neighboring folders (`10-sources` and
  `15-knowledge`), create files with arbitrary names, or hand-edit files
  flagged "AI-generated," breaking a chain that depended on them. Every
  project that repeats this scheme sets up its own `CLAUDE.md` with
  concrete rules (template — [[Project CLAUDE template]]), rather than
  relying on "everyone just knows how it works here." For a team, this
  is complemented by the same "entry points" rule from section 4 — a
  human only writes to `00-inbox` or prepares `20-questions`; sorting
  into the rest of the folders stays the AI's job.
- **Accumulation of stale atomic notes.** Agents that create a file for
  every small question or experiment fill `15-knowledge`/`20-questions`
  with notes over months, some of which have gone stale (a closed
  question, an experiment against a code version that no longer exists).
  This doesn't break the structure immediately, but it gradually
  degrades the quality of the MOC and of search — noise starts getting
  mixed in. Mitigation: a `stale`/`dismissed` status (see
  [[02 Tags, types and statuses]]) treated not as a formality but as a
  trigger for periodic review, not just a label on paper.
- **Version history under Git collaboration.** If the vault syncs
  through Git, frequent automatic agent commits and human edits on the
  same branch produce frequent merge conflicts exactly in the MOC files
  (`plan.md`, `journal.md`) — they change more often than everything
  else. Mitigation outside the structure itself: separate branches per
  agent/role, or a review before merging, rather than an automatic push
  to the main branch.

## Rolling it out step by step

If the scheme above is taken as a launch plan rather than theory:

1. Carve out the technical layer: create `_access/agents_config/` and
   put a system prompt for each role from the table above in it.
2. Set up what triggers the agents — a schedule (say, every N minutes)
   or a trigger on a new file appearing in `00-inbox`; the choice
   depends on the orchestration tool, not on the vault structure itself.
3. Run one simple task end to end, from `00-inbox` to `state.md`, and
   confirm a trace was actually left in `journal.md` at every step,
   before wiring up anything more important to the scheme.

The risks above (rule drift, accumulation of stale notes) aren't a
one-time threat — they show up over time. The regular procedure against
them is [[06 Vault hygiene and review]].
