---
type: knowledge
tags:
  - methodology
  - reference
updated: 2026-09-19
related: "[[00 Foundation of project structure]]"
---

# Tags, types and statuses

A reference of values already appearing in this kit's file frontmatter —
so a new term doesn't get invented where a suitable one already exists.
Convention (section 4 in [[00 Foundation of project structure]]): **the
field key is in Latin/English** (`type`, `status`, `priority`, `id`),
**the value is in plain language**. A project-specific key alias
(`priority`, `updated`) is fine if that's been decided for a particular
project — what matters is not mixing both variants of the same field
within one project.

## `type` — file type

Answers "what kind of document is this," regardless of which project it
lives in.

| Value | Where it's used | Meaning |
|---|---|---|
| `project` | a project's README | a project card — entry point, description, structure |
| `readme` | a README (when not claiming the full methodology) | the same, but without claiming a "full profile" |
| `rules` | `CLAUDE.md` | rules of engagement for the AI agent inside a project |
| `dashboard` | `state.md` | a live MOC snapshot of the current state |
| `plan` | `plan.md` | the current horizon, no checkboxes |
| `journal` | `journal.md` | an append-only log of events |
| `knowledge` | notes in `15-knowledge/` and in `(R) Resources` | an atomic, cleaned-up thought, true regardless of a specific project |
| `source` | files in `10-sources/` | an immutable original, read-only |
| `inbox` | files in `00-inbox/` | raw, unsorted |
| `tasks` | a flat to-do list (projects without Johnny.Decimal) | a checklist with no question cards |
| `daily` | files in `(A) Journal/YYYY-MM-DD.md` | a day note: focus of the day, checklists, incoming log |

Typed entities (`Q-`, `D-`) usually don't carry a `type` — their type is
already visible from the `id`, so duplicating it adds nothing.

## `status` — stage of the document's life

The set of values depends on the entity type — a question and a decision
live through different life cycles.

**Question** (`20-questions/Q-*.md`):

| Value | Meaning |
| --------- | ------------------------------------------------ |
| `open`    | the fork hasn't been resolved yet |
| `answered` | an answer exists, the question can be closed |
| `dismissed` | turned out not to matter — nothing would have changed with an answer |
| `stale`   | the context disappeared, the question is no longer relevant |

**Decision** (`30-decisions/D-*.md`):

| Value | Meaning |
|---|---|
| `proposed` | the AI prepared the decision with a rationale, the human hasn't confirmed it yet |
| `accepted` | the human confirmed it, the decision is in effect |
| `revoked` | the decision was withdrawn with no replacement |
| `superseded` | the decision was withdrawn, but a new `D-NN` exists that references it |

**Project** (a project's `README.md`) — here `status` is freer in form:
a short text description of the current stage, not a fixed enum
("MVP in development," "gathering material," "developing in
parallel"). Reason: projects differ too much in nature (see
[[(P) Projects/01 Example of a mature project/README|01 Example of a mature project]]
vs. [[(P) Projects/02 Example of a simple project/README|02 Example of a simple project]])
for the same stage to be named the same way across all of them. What is
fixed is a separate `priority` field (below), not `status`.

## `priority` — priority

Two independent layers, not to be confused:

**Project priority** (the `priority` field in a project's README) —
rarely changes, answers "what's even being worked on":

| Value | Meaning |
|---|---|
| `1` | in focus — keep 2–4 projects at a time ([[Focus]]) |
| `2` | relevant, but not right now |
| `3` | background — someday |

**Question priority** (the `priority` field in a `Q-*.md` card) —
answers "what matters most inside this project right now":

| Value | Meaning |
|---|---|
| `blocker` | can't move forward on the current plan without an answer |
| `high` | not blocking, but noticeably slows things down |
| `normal` | standard processing pace |
| `someday` | interesting, but not urgent |

Tasks outside question cards (a simple project with no `20-questions`,
for example [[(P) Projects/02 Example of a simple project/Tasks|Tasks]])
use their own priority layer — the Tasks plugin's emoji (`🔺` highest,
`⏫` high, `🔼` medium, no icon for normal/low). These two mechanisms
don't mix: if a project has `20-questions`, priority is read from the
question cards (as in [[Focus]]), not from Tasks emoji.

## `tags` — tags

Tags here are secondary to the folder structure and to the typed fields
above — they help search and grouping, but don't replace `type`/
`status`. Values that appear:

| Tag | Where | Meaning |
|---|---|---|
| `moc/inbox` | root dashboards (`README`, `Focus`, `Task summary`, `Kanban board`) | a top-level live aggregator that stores nothing itself |
| `moc` | `state.md`, `plan.md`, `journal.md`, `structure.md` | a content map inside a project or section |
| `project` | project READMEs | a project card |
| `example` | all test data in this kit | marks the content as demonstrational, not real |
| `methodology` | the "Foundation…"-level files in `(R) Resources` | knowledge about the system itself, not about a project's subject matter |
| `reference` | this file | a list of allowed values, not a standalone thought |
| `ai`, `policy` | `CLAUDE.md` | rules for the AI agent |

## How to add a new value

If a project needs a value not on this list — add it here too, rather
than leaving it in just one file: the reference loses its purpose if it
doesn't reflect every value actually in use across the vault.
