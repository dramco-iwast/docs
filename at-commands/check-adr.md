---
layout: default
title: Check LoRa Adaptive Data Rate (ADR)
parent: AT Commands
has_toc: true
nav_order: 6
---

## Check Data Accumulation
### Command
```
AT+ADR?
```

### Response
```
+ADR: <0|1>
```

### Description
Check whether or not the ADR option is enabled for the LoRa communication (requires confirmd messages).


### Example
```
Command> AT+ADR?
Response> +ADR: 1
```
ADR is enabled for the LoRa communication.
