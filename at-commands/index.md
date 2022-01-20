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

| Parameter    | Format |
| ------------ | ------ |
| Baudrate     | 115200 |
| data bits    | 8      |
| parity       | none   |
| stop bits    | 1      |
| flow control | off    |
|-----------|--------|-------------|




## Data Format and Identifiers

| Parameter | Format | Description |
|-----------|--------|-------------|
| `<sensor-id>` | 4 hex digits | The Sensor ID comprises the Sensor Address (given by the motherboard) and the Sensor Type |
| `<sensor-address>` | 2 hex digits | First 2 hex digits in the sensor id. |
| `<sensor-type>` | 2 hex digits | Last 2 hex digits in the sensor id. IDs are defined in [sensors.yaml](https://github.com/dramco-iwast/sensor-description-files/blob/master/sensors.yaml) |
| `<metric-id>` | 2 hex digits | TODO |
| `<motherboard-id>` | 4 hex digits | The 16-bit motherboard ID is identicatl to the last 16 bits of the `<lora-dev-eui>` |
| `<lora-dev-eui>` | 16 hex digits | A 16-character string representing an 8-byte identifier in hexadecimal notation. Typically, this can be copied straight from the TTN end device settings page. |
| `<lora-app-key>` | 32 hex digits | A 32-character string representing an 16-byte key in hexadecimal notation. Typically, this can be copied straight from the TTN end device settings page. |
|-----------|--------|-------------|


## Error Codes

| Parameter              | Format   | Description                                                                                |
| ---------------------- | -------- | ------------------------------------------------------------------------------------------ |
| `<AT_UNDEFINED_ERROR>` | 0        | We could not identify the error, but there is one...                                       |
| `<AT_INVALID_ID>`      | 1        | The specified identifier (address, type or id) is not valid                                |
| `<AT_INVALID_POL>`     | 2        | The polling interval does not comply with the specs                                        |
| `<AT_WRONG_VALUE>`     | 3        | The supplied value is not supported, e.g. when enabling something only 0 and 1 are allowed |
| `<AT_WRONG_COMMAND>`   | 4        | The supplied AT command is not recognized                                                  |
| `<AT_WRONG_ARG_LENGTH>`| 5        | The AT command argument has an unexpected length                                           |
| ---------------------- | -------- | ------------------------------------------------------------------------------------------ |



