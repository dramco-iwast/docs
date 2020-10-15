---
title: Message format
parent: Motherboard
has_toc: true
nav_order: 2
layout: default
---

LoRaWAN message format used by the motherboard

| Field                 | Size             | Description |
|:----------------------|:----------------:|:------------|
| `<message-type>`      | 1 byte           | The Message Type field indicates what type of message has been sent. |
| `<message-payload>`   | 3 up to 47 bytes | The payload format depends on the Message Type.|

## Supported message types:

1. Immediate Data: message type 'I'
2. Accumulated Data: message type 'A'
3. Status Message: message type 'S'

## Immediate data message format

If no data accumulation is being used, the motherboard will send sensor readings from the moment
they become available. The message, however, can still contain readings from different sensors. This
happens, for example, when two sensors are polled at the same moment.

| Field                 | Size             | Description / Value |
|:----------------------|:----------------:|:--------------------|
| `<message-type>`      | 1 byte           | 'I' (0x49) for an immediate data message. |
| `<sensor-data>`       | NS*(1+2*NMi)     | Sensor measurment data formated as below. |

* NS is the number of sensors that have their data ready for transmission to the back-end server.
* NMi is the number of metrics supported by the i-th sensor (see the individual sensor description files), where 1 < i < NS.

### Sensor data format (immediate)

The sensor-data field of an immediate data message is comprised of NS frames. Each frame is formated
according to the table below.

| Field                 | Size             | Description / Value |
|:----------------------|:----------------:|:--------------------|
| `<sensor-address>`    | 1 byte           | The sensors' I2C address. |
| `<sensor-readings>`   | 2*NM   | Two data bytes for each metric supported by the sensor. |

## Accumulated data message format

If data accumulation is being used, the motherboard will accumulate sensor readings and send them
when the payload size threshold is exceeded.

| Field                 | Size             | Index      | Description / Value |
|:----------------------|:----------------:|:----------:|:--------------------|
| `<message-type>`      | 1 byte           | 0          | 'A' (0x41) for an immediate data message. |
| `<sensor-data>`       | NS*(3+2*NMi)     | Sensor measurment data formated as below. |

* NS is the number of sensors that have their data ready for transmission to the back-end server.
* NMi is the number of metrics supported by the i-th sensor (see the individual sensor description files), where 1 < i < NS.

### Sensor data format (accumulated)

The sensor-data field of an accumulated data message is comprised of NS frames. Each frame is formated
according to the table below.

| Field                 | Size             | Description / Value |
|:----------------------|:----------------:|:--------------------|
| `<sensor-address>`    | 1 byte           | The sensors' I2C address. |
| `<seconds-elapsed>`   | 2 byte           | Seconds elapsed since the previous measurment. |
| `<sensor-readings>`   | 2*NM   | Two data bytes for each metric supported by the sensor. |

The seconds-elapsed field indicates how many seconds have passed since a previous measurment (of any
sensor). This field is always zero for the first sensor in the sensor-data field.

## Status message format

The motherboard will send a status message every 12 hours to the back-end server.

| Field                 | Size             | Index      | Description / Value |
|:----------------------|:----------------:|:----------:|:--------------------|
| `<message-type>`      | 1 byte           | 0          | 'S' (0x53) for a status message. |
| `<motherboard-id>`    | 2 bytes          | 1-2        | The 16-bit Motherboard ID.|
| `<local-epoch>`       | 4 bytes          | 3-6        | A 32-bit UNIX timestamp representing the local time of the motherboard. |
| `<data-accumulation>` | 1 byte           | 7          | `<0x01 | 0x00 >` Indicating if data accumulation is used or not (resp.). |
| `<nr-of-sensors>`     | 1 byte           | 8          | A value representing the number of sensors connected to the motherboard. |
