---
id: D-001
status: accepted
closes: null
date: 2026-09-16
---

# D-001. Controller — ESP32, not Raspberry Pi Zero

## Context

Need a controller for one greenhouse: read one moisture sensor, drive
one pump relay. A Raspberry Pi Zero was the initial choice out of habit
(already used in another project).

## Decision

Use an ESP32 instead of a Raspberry Pi Zero.

## Rationale

- ESP32 is cheaper (~$4 vs ~$15) and doesn't need an SD card or a full OS;
- the task doesn't need Linux — just ADC polling and GPIO control over
  Wi-Fi;
- ESP32 power draw is far lower — matters since it's powered from the
  same circuit as the pump.

## Rejected alternatives

| Option | Why rejected |
|---|---|
| Raspberry Pi Zero | overkill for the task, more expensive, needs an SD card and OS boot |
| Arduino Uno without Wi-Fi | no built-in connectivity, needs a separate Wi-Fi module — adds complexity with no upside |

## Consequences

Code is written in the Arduino framework (C++), not Python — affects all
later experiments and knowledge notes about this project.

## What new facts would prompt a revisit

If there's ever more than one greenhouse and a local aggregation server
is needed — then a shared Raspberry Pi as a hub could make sense
alongside several ESP32s, not instead of them.
