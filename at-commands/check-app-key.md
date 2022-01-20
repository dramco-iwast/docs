---
layout: default
title: Check the LoRa Application Key
parent: AT Commands
has_toc: true
nav_order: 10
---

## Check Data Accumulation
### Command
```
AT+APK?
```

### Response
```
+APK: <lora_app_key>
```

### Description
Check what the LoRa application key is for this motherboard.


### Example
```
Command> AT+APK?
Response> +APK: FFFFAAFF11EE22DD33CC447600005555
```
The motherboard will use `FFFFAAFF11EE22DD33CC447600005555` as LoRa application key. This key is used during the over-the-air activation (OTAA) network join procedure.
