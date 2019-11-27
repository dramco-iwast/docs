---
title: AT Commands
has_toc: true
has_children: true
nav_order: 3
layout: default
---


## Serial Communication

When the motherboard is powered on (due to a power cycle), it starts listening (serial) for 10 seconds.
If there is no incoming data in that window, the serial communication is stopped.
A power cycle is required, to re-enter this phase, so it can receive AT commands.

All AT commands changing the configuration of the sensors, will be stored in non-volatile memory.
To push these configurations to sensors, the `close` command needs to be executed.
This will also halt the serial communication, as the motherboard does not process any incoming data.


## Data Format and Identifiers
| Parameter | Format | Description |
|-----------|--------|-------------|
| Sensor ID | 2 hex digit | |
| metric ID | 2 hex digit | |

