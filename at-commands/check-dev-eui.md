---
layout: default
title: Check the LoRa Device EUI
parent: AT Commands
has_toc: true
nav_order: 8
---

## Check Data Accumulation
### Command
```
AT+EUI?
```

### Response
```
+EUI: <the_lora_dev_eui>
```

### Description
Check what the LoRa device EUI is for this motherboard.


### Example
```
Command> AT+ADR?
Response> +ADR: FF11EE22DD33CC44
```
The motherboard has `FF11EE22DD33CC44` as LoRa device EUI (and the motherboard ID is `CC44`).
