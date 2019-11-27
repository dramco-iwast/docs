---
layout: default
title: Set threshold
parent: AT Commands
has_toc: true
nav_order: 5
---

## Set poll interval

### Command
```
AT+TH=<sensor-id> <metric> <enable>
```

### Response
```
OK | ERROR <code>
```

### Description
Set the threshold for the sensor with ID `<sensor-id>`. The `<sensor-id>` field and the `<metric>` are each a 2-digit hex string. The `<threshold>` is `0` when disabled and `1` when enabled. When the threshold is changed successfully, the motherboard responds with `OK`. Otherwise, e.g., when an invalid sensor ID is specified, the response is `ERROR` followed by an error code.

### Example
```
Command>  AT+TH=01 01 0
Response> OK
```
Disable the threshold for metric `0x01` of sensor `0x01`.
