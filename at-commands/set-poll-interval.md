---
layout: default
title: Set poll interval
parent: AT Commands
has_toc: true
nav_order: 11
---

## Set poll interval

### Command
```
AT+POL=<sensor-address> <metric> <poll-interval>
```

### Response
```
OK | ERROR <code>
```

### Description
Set the poll interval for the sensor with ID `<sensor-address>`. The `<sensor-address>` field and the `<metric-id>` are each a 2-digit hex string. The `<poll-interval>` formatted as a decimal string. When the poll interval is changed successfully, the motherboard responds with `OK`. Otherwise, e.g., when an invalid sensor ID is specified, the response is `ERROR` followed by an error code.

> Bedenkingen geof (maar moet dat hier)?
>•	Minimum poll interval: 5 minutes? (Not enforced yet in software).
>•	Maximum value 65535 (approx.. 18 hours).
>•	A poll interval of 0 will be treated as “never poll”, sensor will operate threshold-based.

### Example
```
Command>  AT+POL=01 01 600
Response> OK
```
Set poll interval for sensor 0x01, metric 0x01 to 600 seconds, i.e., every 10 minutes.

