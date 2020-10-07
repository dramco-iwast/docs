---
layout: default
title: Check Data Accumulation
parent: AT Commands
has_toc: true
nav_order: 4
---

## Set Data Accumulation (get motherboard ID)
### Command
```
AT+ACC?
```

### Response
```
+ACC: <0|1>
```

### Description
Check whether or not the motherboard will accumulate sensor measurements before transmitting them.


### Example
```
Command> AT+AGG?
Response> +ACC: 0
The board will not use data accumulation.
```
