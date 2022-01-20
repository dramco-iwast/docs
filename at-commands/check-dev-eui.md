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
Check what the LoRa device EUI is for this motherboard. If the EUI has not been set before, this might return either an empty string or just plain nonsense. Use this command only to verify what the EUI is, if it has been set before.


### Example
```
Command> AT+EUI?
Response> +EUI: FF11EE22DD33CC44
```
The motherboard has `FF11EE22DD33CC44` as LoRa device EUI (and the motherboard ID is `CC44`).
