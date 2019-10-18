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
Ping the motherboard. The motherboard will respond with its motherboard ID This is a sixteen bit unsigned identifier. The ID is sent as a 4-digit hex string in ASCII format.


### Example
```
Command>  AT+PNG?
Response> +PNG: 474F
The board has id 0x474F
```
