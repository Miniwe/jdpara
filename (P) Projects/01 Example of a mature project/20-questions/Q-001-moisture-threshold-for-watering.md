---
id: Q-001
status: open
priority: high
created: 2026-09-17
---

# Q-001. At what soil moisture percentage should watering turn on

## Question

The sensor datasheet gives raw ADC units (0–4095), not percentages. The
"air / water" calibration produced a range that doesn't match the
manufacturer's datasheet examples — unclear which to trust.

## What changes with the answer

The answer determines a specific number in the controller logic: below
what ADC value watering starts. Without an answer, auto-watering can't
be turned on safely — either the greenhouse floods or nothing gets
watered at all.

## Context

Calibration done on 2026-09-17, values recorded in
[[10-sources/2026-09-17-sensor-calibration]].

## Next step

Water a test pot by hand until it looks "visibly moist" and record the
ADC reading at that point — getting a personal reference point instead
of relying on the documentation.
