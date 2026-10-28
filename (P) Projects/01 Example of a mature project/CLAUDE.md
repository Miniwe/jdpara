---
type: rules
tags: [ai, policy, example]
---

# CLAUDE.md — rules of work in this folder

**Test data.** Project: greenhouse watering tracker — moisture sensors,
pump, watering log.

When starting work, read [[JDPARA-EN/(P) Projects/01 Example of a mature project/state]] — what's gathered so far, what's
confirmed. Then [[plan]] (current horizon), [[JDPARA-EN/(P) Projects/01 Example of a mature project/README]] (entry point).

## Where things go

| What | Where |
|---|---|
| A fact from sensor/controller documentation | `15-knowledge/` (not yet started in this example — will appear with the first note) |
| A fork, a missing detail | `20-questions/Q-NNN-name.md` |
| A choice made, with rationale | `30-decisions/D-NNN-name.md` |
| An excerpt from a datasheet, verbatim | `10-sources/` — do not edit after it's recorded |
| Unsorted material | `00-inbox/` |

## Required frontmatter fields

Keys in Latin, values in plain English — see examples in `20-questions/`
and `30-decisions/` of this project.

## Secrets

The greenhouse Wi-Fi password and the MQTT broker token never go in here
— only the controller's environment variable names.

## History of rules

- **2026-09-19** — file created from the template
  [[Project CLAUDE template|JDPARA-EN/(R) Resources/_templates/Project CLAUDE template]].
