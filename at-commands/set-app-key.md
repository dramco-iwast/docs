---
layout: default
title: Set the LoRa Application Key
parent: AT Commands
has_toc: true
nav_order: 9
---

## Set Data Accumulation
### Command
```
AT+APK=<lora_app_key>
```

### Response
```
OK | ERROR <code>
```

### Description
Set the LoRa Application for this motherboard. The `<lora_app_key>` field is sent as a **32-digit hex string** in ASCII format as defined [here](../at-commands). This keyshould match the OTAA settings for your TTN application.

### Example
```
Command> AT+APK=FFFFAAAA6666DDDD1234987600005555
Response> OK
```
There LoRa application key is now set to `FFFFAAAA6666DDDD1234987600005555`.

