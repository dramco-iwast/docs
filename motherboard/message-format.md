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

| Field                 | Size               | Description / Value                       |
|:----------------------|:------------------:|:------------------------------------------|
| `<message-type>`      | 1 byte             | 'I' (0x49) for an immediate data message. |
| `<sensor-data>`       | NS*(1+2*NMi) bytes | Sensor measurment data formated as below. |

* NS is the number of sensors that have their data ready for transmission to the back-end server.
* NMi is the number of metrics supported by the i-th sensor (see the individual sensor description
files), where 1 < i < NS.

### Sensor data format (immediate)

The sensor-data field of an immediate data message is comprised of NS frames. Each frame is formated
according to the table below.

| Field                 | Size        | Description / Value                                     |
|:----------------------|:-----------:|:--------------------------------------------------------|
| `<sensor-address>`    | 1 byte      | The sensors' I2C address.                               |
| `<sensor-readings>`   | 2*NM bytes  | Two data bytes for each metric supported by the sensor. |

### Examples of an immediate data message
Lets assume that the sensor with address 0x52 supports two metrics, then the sequence of bytes shown 
below is a possible immediate data message.

`{ 0x49, 0x52, 0x00, 0x01, 0x12, 0x04 }`

This packet contains the data of 1 sensor. 
* The first byte indicates that it is an immediate data message.
* The second byte indicates the address, i.e., 0x52.
* The next two bytes represent the reading of the first metric, i.e., 0x0001.
* The last two bytes represent the reading of the second metric, i.e., 0x1204.

**Note:** the sensor-description-files contain information about what (how many) metrics are 
supported and how the readings need to be interpreted.

## Accumulated data message format

If data accumulation is being used, the motherboard will accumulate sensor readings and send them
when the payload size threshold is exceeded.

| Field                 | Size               | Description / Value                       |
|:----------------------|:------------------:|:------------------------------------------|
| `<message-type>`      | 1 byte             | 'A' (0x41) for an immediate data message. |
| `<sensor-data>`       | NS*(3+2*NMi) bytes | Sensor measurment data formated as below. |

* NS is the number of sensors that have their data ready for transmission to the back-end server.
* NMi is the number of metrics supported by the i-th sensor (see the individual sensor description
files), where 1 < i < NS.

### Sensor data format (accumulated)

The sensor-data field of an accumulated data message is comprised of NS frames. Each frame is
formated according to the table below.

| Field                 | Size        | Description / Value                                     |
|:----------------------|:-----------:|:--------------------------------------------------------|
| `<sensor-address>`    | 1 byte      | The sensors' I2C address.                               |
| `<seconds-elapsed>`   | 2 byte      | Seconds elapsed since the previous measurment.          |
| `<sensor-readings>`   | 2*NM bytes  | Two data bytes for each metric supported by the sensor. |

The seconds-elapsed field indicates how many seconds have passed since a previous measurment (of any
sensor). This field is always zero for the first sensor in the sensor-data field.

### Examples of an accumulated data message

Lets assume that the sensor with address 0x52 supports two metrics and the sensor with address 0x48 
supports 1 metric, then the sequence of bytes shown below is a possible immediate data message.

`{ 0x41, 0x48, 0x00, 0x00, 0x54, 0x09, 0x52, 0x00, 0x3C, 0xAE, 0x20, 0x15, 0x62, 0x48, 0x0D, 0xD4, 0x11, 0xBB }`

This packet contains 3 measurements.
* The first byte indicates that it is an accumulated data message.
* The next 5 bytes is the oldest measurement. Of these 5 bytes:
	* the first byte indicates the address, i.e., 0x48.
	* the next two bytes is the number of seconds since the previous measurement, i.e., 0x0000 (0 seconds). This is always 0 for the earliest (first) measurement in the packet.
	* the last two bytes represent the reading of the sensor's only metric, i.e., 0x5409.
* The next 7 bytes is the oldest measurement. Of these 7 bytes:
	* the first byte indicates the address, i.e., 0x52.
	* the next two bytes is the number of seconds since the previous measurement, i.e., 0x003C (60 seconds).
	* the next two bytes represent the reading of the first metric, i.e., 0xAE20.
	* the last two bytes represent the reading of the second metric, i.e., 0x1562.
* The last 5 bytes is the oldest measurement. Of these 5 bytes:
	* the first byte indicates the address, i.e., 0x48.
	* the next two bytes is the number of seconds since the previous measurement, i.e., 0x0DD4 (3540 seconds). This is 3600 seconds (1 hour) later than this sensor's previous measurement.
	* the last two bytes represent the reading of the sensor's only metric, i.e., 0x11BB.

**Note:** the sensor-description-files contain information about what (how many) metrics are 
supported and how the readings need to be interpreted.

## Status message format

The motherboard will send a status message every 12 hours to the back-end server.

| Field                   | Size      | Description / Value                                                      |
|:------------------------|:---------:|:-------------------------------------------------------------------------|
| `<message-type>`        | 1 byte    | 'S' (0x53) for a status message.                                         |
| `<motherboard-id>`      | 2 bytes   | The 16-bit Motherboard ID.                                               |
| `<local-epoch>`         | 4 bytes   | A 32-bit UNIX timestamp representing the local time of the motherboard.  |
| `<data-accumulation>`   | 1 byte    | `<0x01 | 0x00 >` Indicating if data accumulation is used or not (resp.). |
| `<nr-of-sensors>`       | 1 byte    | A value representing the number of sensors connected to the motherboard. |
| `{sensor-address-list}` | NS bytes  | I2C address (1 byte) for each connected sensor.                          |

### Example of a status message

If the back-end server receives the following status message,

`{ 0x53, 0x47, 0x4F, 0x1A 0xC8, 0x1B, 0xE1, 0x00, 0x02, 0x48, 0x52 }`

it can determine that:

* the motherboard has ID 0x474F.
* the local time is 0x1AC81BE1 (449321953 or Wednesday 28 March 1984 11:39:13 GMT). The main purpose is to be able to determine the elapsed time between two status message.
* the motherboard does not use data accumulation.
* two sensors are connected to the motherboard, one with address 0x48 and one with address 0x52.