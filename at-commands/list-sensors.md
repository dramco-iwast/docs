---
layout: default
title: List Sensors
parent: AT Commands
has_toc: true
nav_order: 2
---

## List sensors

### Command
```
AT+LS?
```

### Response
```
+LS: {<sensor1> <sensor2> ...}
```

### Description
List the sensors that are connected to the motherboard. The motherboard will respond with a space-separated list of sensors. In case no sensors are connected this list is empty. The `<sensorX>` field is sent as a **4-digit hex string** in ASCII format as defined [here](/at-commands).For a list of supported sensor types, see the [sensor boards doc](/sensorboards).
Based on the sensor type, the UI can determine which metrics are supported.
  
### Example
```
Command> AT+LS?
Response> +LS: 0168 0221
Two sensors are connected. Sensor 0x01 has type 0x68, sensor 0x02 has type 0x21.
```
