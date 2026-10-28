---
type: plan
updated: 2026-09-19
tags: [moc, example]
---

# Plan — 2-week horizon

**Test data.** Goals and readiness criteria. No checkboxes here —
completed work is recorded in [[JDPARA-EN/(P) Projects/01 Example of a mature project/state]] and [[JDPARA-EN/(P) Projects/01 Example of a mature project/journal]].

## Horizon goal

Build a working prototype: sensor → controller → watering decision →
pump activation, with no cloud backend — everything local, in the
greenhouse.

## Readiness criteria

- the controller gets a sensor reading at least once every 5 minutes;
- the pump turns on automatically when the reading drops below the
  agreed threshold (depends on [[Q-001-moisture-threshold-for-watering]]);
- every pump activation leaves a line in [[JDPARA-EN/(P) Projects/01 Example of a mature project/journal]].

## Condition for the next horizon

The prototype runs without manual intervention for 3 days straight.
