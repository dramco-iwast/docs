---
layout: default
title: Set threshold
parent: AT Commands
has_toc: true
nav_order: 5
---

## Set threshold interval

### Commands


### Enabling
```
AT+TE=<sensor-address> <metric> <thresholds-enabled> 
```

### Threshold Low

```
AT+TLL=<sensor-address> <metric> <threshold-level-low>
```
### Threshold High

```
AT+TLH=<sensor-address> <metric> <threshold-level-high>
```


### Response
```
OK | ERROR <code>
```

### Description
Set the threshold for the sensor with ID `<sensor-address>`. The `<sensor-address>` field and the `<metric>` are each a 2-digit hex string. The `<thresholds-enabled>` is `0` when disabled and `1` when enabled. When the threshold is changed successfully, the motherboard responds with `OK`. Otherwise, e.g., when an invalid sensor ID is specified, the response is `ERROR` followed by an error code. 

### Example
```
Command>  AT+TH=01 01
Response> OK
```
Disable the threshold for metric `0x01` of sensor `0x01`. 

