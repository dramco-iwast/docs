---
layout: default
title: Close
parent: AT Commands
has_toc: true
nav_order: 15
---

## Close
### Command
```
AT+CLS
```

### Response
```
OK | ERROR <error-code>
```

### Description
Close the configuration context.
The motherboard will stop listening to serial communication, enabling to enter a low power state.
It will push the updated configurations to all connected sensors.

### Example
```
Command> AT+CLS
Response> OK
```
No errors occurred. The board has stored the update configuration in its non-volatile memory and will proceed to its normal operation.
