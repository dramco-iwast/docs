---
layout: default
title: Set Data Accumulation
parent: AT Commands
has_toc: true
nav_order: 3
---

## Set Data Accumulation (get motherboard ID)
### Command
```
AT+ACC=<0|1>
```

### Response
```
OK | ERROR <code>
```

### Description
Set whether or not the motherboard will accumulate sensor measurements before transmitting them.


### Example
```
Command> AT+AGG=1
Response> OK
The board will use data accumulation.
```