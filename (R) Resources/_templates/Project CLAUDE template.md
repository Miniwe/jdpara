---
type: rules
tags: [ai, policy]
---

# CLAUDE.md — rules of work in this folder

Project: {{short description of the project's subject}}.

When starting work, read [[state]] — what's gathered so far, what's
confirmed. Then [[plan]] (current horizon), [[README]] (entry point, map
of knowledge).

## Where things go

| What | Where |
|---|---|
| A fact from a source/the code: how something works, a mechanism | `15-knowledge/` — one page per topic |
| A missing detail, a fork | `20-questions/Q-NNN-name.md` |
| A choice made, with rationale | `30-decisions/D-NNN-name.md` |
| An excerpt from a source, verbatim | `10-sources/` — do not edit after it's recorded |
| Unsorted material | `00-inbox/` |

File names: lowercase, hyphen-separated, in English. Q/D numbering is
sequential, never reused.

## Required frontmatter fields

Keys in Latin, values in plain English.

**Question:**
```yaml
id: Q-001
status: open           # open / answered / dismissed
priority: normal        # blocker / high / normal / someday
created: YYYY-MM-DD
```
The body must include: the question itself, **what changes with the
answer**, the next step. If no action would change based on the answer —
the question doesn't get created.

**Decision:**
```yaml
id: D-001
status: proposed        # proposed / accepted / revoked / superseded
closes: Q-001
date: YYYY-MM-DD
```
The body: context, the decision, **rationale**, rejected alternatives and
why, what it makes irreversible. Decisions aren't deleted — if the
choice changes, a new one gets created, and the old one gets status
`superseded`.

## Source rule

Every fact in `15-knowledge` links back to the source file or line. A
discrepancy between a source and a fact is a reason to fix the knowledge
note and flag it in [[journal]], not to rewrite the source.

## Secrets

Nothing secret goes in here — not values, not variable names, if the
variable itself is the secret. Passwords, tokens, keys — in a password
manager or `.env` outside this vault.

## History of rules

- **YYYY-MM-DD** — file created from the [[Project CLAUDE template]]
  template in `JDPARA-EN`.
