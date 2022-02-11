---
layout: default
title: Set the LoRa Device EUI
parent: AT Commands
has_toc: true
nav_order: 7
---

##  Set the LoRa Device EUI
>> Note that the AppEUi or JoinEUI is correctly entered (fixed value): 4957415354415050
>> 
### Command
```
AT+EUI=<lora_dev_eui>
```

### Response
```
OK | ERROR <code>
```

### Description
Set the LoRa Device EUI for this motherboard. The `<lora_dev_eui>` field is sent as a **16-digit hex string** in ASCII format as defined [here](../at-commands). This device EUI should match the settings for your TTN application. The 16-bit motherboard ID is the same as the last four digits of the device EUI.

### Example
```
Command> AT+AEUI=0123456789ABCDEF
Response> OK
```
There LoRa device EUI is set to `0123456789ABCDEF`.

