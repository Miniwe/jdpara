---
type: knowledge
tags:
  - methodology
  - moc
updated: 2026-09-19
related: "[[01 Scaling the foundation]]"
---

# Vault hygiene and review

[[01 Scaling the foundation]] names the risks the structure doesn't
solve on its own — rule drift, accumulation of stale notes, agent
addressing mistakes — but describes them as a warning, not a procedure.
This document turns those risks into a concrete, repeatable ritual: what
to check, how often, and by what signs.

## 1. Why review, if the structure is already strict

Strict addressing (Johnny.Decimal) and explicit statuses (the "status"
section in [[02 Tags, types and statuses]]) remove the question "where
does this go," but not the question "is what's already there still
true?" A question can sit at `open` for years even though its answer was
effectively found long ago; a decision can be `accepted` even though the
conditions under which it was made have changed. The structure doesn't
go stale on its own — the statuses inside it do, and without periodic
review the system looks alive while lying about its own state.

## 2. What to check

Broken down by entity type — each check answers its own question.

**Questions (`20-questions/Q-*.md`)**

- Are there `open` questions whose actual answer is already visible from
  a later `30-decisions` entry or from `journal.md`? Their status should
  move to `answered`, instead of silently hanging.
- Are there `open` questions missing the "What changes with the answer"
  section (required by the rule in section 4 of [[00 Foundation of
  project structure]])? That's a signal the question was created out of
  habit, not because an answer would actually change anything — a
  candidate for `dismissed`.
- Are there questions whose project context has disappeared (the
  project archived, the feature dropped)? Status should become `stale`,
  not stay `open` after the fact (see section 4 in [[05 Project
  lifecycle]]).

**Decisions (`30-decisions/D-*.md`)**

- Are there `accepted` decisions that have effectively been replaced by
  a newer decision with no explicit `superseded` link? Add the
  connection, rather than leaving two "active" decisions on the same
  question at once.
- Does every decision have "Rationale" and "Rejected alternatives" in
  place (required by section 4 in [[00 Foundation of project
  structure]])? A decision with no rationale is a signal it was created
  in a hurry and never reviewed by a human.

**Frontmatter and types**

- Do `type`/`status`/`tags` values match what's already described in
  [[02 Tags, types and statuses]], or has a new value quietly started
  being used that the reference doesn't know about? A new value isn't a
  mistake by itself, but it needs to be added to the reference — otherwise
  the next review (human or AI) won't know what it means.
- Is `status` being mixed with a differently-spelled version of the same
  field in one project without reason — the rule from section 4 in
  [[00 Foundation of project structure]] about key consistency.

**MOC and links**

- Do `state.md`/`plan.md` contain links to files that no longer exist
  (moved, renamed, archived)? An orphaned link in a MOC is worse than a
  missing one — it creates the appearance of an up-to-date map.
- Are there atomic notes in `15-knowledge`/`(R) Resources` that no MOC
  and no other note links to? Not necessarily something to delete — but
  worth a deliberate decision, rather than leaving it as an accidental
  orphan.

## 3. Who runs the review, and when

Review isn't a one-off cleanup, it's a rhythm tied to the same priority
cycle described in [[05 Project lifecycle]]:

- **On a project priority change** (especially `2 → 1`, section 3 in
  [[05 Project lifecycle]]) — a natural point to check `state.md` before
  the project enters active work.
- **On closing/archiving a project** (section 4 in [[05 Project
  lifecycle]]) — reviewing question and decision statuses here isn't
  optional, it's part of closing itself, not a separate follow-up
  action.
- **On a schedule for the whole vault**, independent of individual
  projects — frequency depends on pace: an active vault (several
  projects at `priority: 1`) needs it more often than a quiet one. The
  exact cadence is a project/human decision, not part of the
  methodology; what matters is that it's written down somewhere explicit
  (for example, in the vault's general `CLAUDE.md` or its `README.md`),
  not held only in memory.

In a multi-agent scenario (the "Scaling to multi-agent scenarios"
section in [[01 Scaling the foundation]]), this role matches the
Supervisor/navigator — the one with read access to the whole vault and
write access to the MOC files. Review isn't a separate fifth role, it's
part of the Supervisor's already-described responsibility, performed on
a schedule rather than only reactively.

## 4. What a review should not do

- **Not rewrite the journal.** The "journal only grows downward" rule
  (section 4 in [[00 Foundation of project structure]]) still applies
  during a review — an error found in an old `journal.md` entry gets
  fixed with a new line, not a correction to the old one.
- **Not delete decisions outright.** A stale decision gets a
  `superseded`/`revoked` status with a rationale (section 4 in
  [[00 Foundation of project structure]]) — the same rule that bars the
  AI from making decisions on the human's behalf also bars silently
  deleting ones already accepted.
- **Not become an excuse for extra files.** A review doesn't have to
  spawn a `Q-NN` card for every inaccuracy it finds — if the fix is
  trivial (update a status, fix a link), it's applied directly; a
  question only gets created when the decision is genuinely unclear and
  "what changes with the answer" (section 4 in [[00 Foundation of
  project structure]]) is something other than the fix itself.

## Summary

Review isn't a new layer of methodology on top — it's a regular check
that the statuses, links, and types described in [[00 Foundation of
project structure]] and [[02 Tags, types and statuses]] still match
reality. Without it, the risks named in [[01 Scaling the foundation]]
don't go away — they just stay invisible until someone tries to trust a
map that's already out of date.
