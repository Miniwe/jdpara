---
id: Q-002
status: open
priority: blocker
created: 2026-09-19
---

# Q-002. MQTT or HTTP for sensor-to-controller communication

## Question

The sensor datasheet shows support for both MQTT and plain HTTP
requests. The protocol choice determines what to write on the
controller side and whether a local MQTT broker is needed.

## What changes with the answer

MQTT requires standing up a broker (one more service in a greenhouse
that already only has the ESP32) and setting up topics. HTTP is simpler
for a single controller but scales worse if there's ever more than one
sensor. Without an answer, the sensor-polling code can't be written — it
blocks the entire current plan horizon.

## Context

[[10-sources/2026-09-17-sensor-calibration]] — same datasheet.

## Next step

Check whether the ESP32 can run an MQTT client and the Wi-Fi stack at
the same time without running out of memory — if not, the question
resolves itself in favor of HTTP.
