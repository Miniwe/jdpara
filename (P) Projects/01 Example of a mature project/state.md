---
type: dashboard
updated: 2026-09-19
tags: [moc, example]
---

# Project state

**Test data.** Snapshot as of 2026-09-19.

## Status lights

| Area | State | Determined by |
|---|---|---|
| Controller (ESP32) | 🟢 | firmware flashed, responds to ping |
| Moisture sensor | 🟡 | connected, calibration not verified |
| Pump | 🟠 | relay wired, activation by command not tested live |
| Watering logic | ⚪ | waiting on [[Q-001-moisture-threshold-for-watering]] |
| Communication protocol | 🟠 | waiting on [[Q-002-sensor-protocol]] |

## Decisions

**Accepted** (1)
- [[D-001-esp32-as-controller]] — ESP32 controller

**Proposed** (0)

## Questions

**Blocking**
- [[Q-002-sensor-protocol]]

**Open, not blocking**
- [[Q-001-moisture-threshold-for-watering]]

## What's still unverified

- live pump activation by command from the controller;
- sensor behavior below 5°C (not covered in the spec).
