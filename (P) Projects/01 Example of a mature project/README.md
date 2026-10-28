---
type: project
status: MVP in development
priority: 1
updated: 2026-09-19
tags: [project, example]
---

# Example of a mature project

**Test data.** Demo project "greenhouse watering tracker": moisture
sensors send readings, the app decides when to turn on the pump, and
keeps a watering log. Used to show what a project looks like after
several work sessions: with accumulated questions, decisions made, and a
live status dashboard.

## A new session starts here

1. [[JDPARA-EN/(P) Projects/01 Example of a mature project/state]] — what's gathered so far, what's confirmed, what isn't
2. [[plan]] — the current horizon
3. [[JDPARA-EN/(P) Projects/01 Example of a mature project/journal]] — timeline

## Structure

```
README.md          ← this file
CLAUDE.md           ← rules of work for the AI agent
state.md            ← dashboard
plan.md             ← current horizon, no checkboxes
journal.md          ← append-only log
00-inbox/           ← raw, unsorted
10-sources/         ← immutable originals
20-questions/       ← open forks, prefix Q-
30-decisions/       ← fixed choices, prefix D-
```

## Open questions

| | Priority | About |
|---|---|---|
| [[Q-001-moisture-threshold-for-watering]] | high | no data on what soil moisture % should trigger watering |
| [[Q-002-sensor-protocol]] | blocker | whether the sensor reports over MQTT or HTTP — determines the backend |

## Decisions

| | |
|---|---|
| [[D-001-esp32-as-controller]] | ESP32 instead of a Raspberry Pi Zero — cheaper and enough for one greenhouse |
