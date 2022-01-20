---
layout: default
title: Ping
parent: AT Commands
has_toc: true
nav_order: 1
---

## Ping (get motherboard ID)
### Command
```
AT+PNG?
```

### Response
```
+PNG: <motherboard-id>
```

### Description
Ping the motherboard. The motherboard will respond with the version of the firmware.


### Example
```
Command> AT+PNG?
Response> +PNG: IWAST v2022_January_001
```
The motherboard is running the IWAST `v2022_January_001` firmware
