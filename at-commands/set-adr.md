---
layout: default
title: Set LoRa Adaptive Data Rate (ADR)
parent: AT Commands
has_toc: true
nav_order: 5
---

## Set Data Accumulation
### Command
```
AT+ADR=<0|1>
```

### Response
```
OK | ERROR <code>
```

### Description
Set whether or not the ADR option is enabled for the LoRa communication (requires confirmd messages).


### Example
```
Command> AT+ADR=0
Response> OK
```
There is no Adaptive Data Rate for the Lora Communication. The default datarate will be used (typically SF11_BW125).

