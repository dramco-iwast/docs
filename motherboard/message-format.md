---
title: Message format
parent: Motherboard
has_toc: true
nav_order: 2
layout: default
---

LoRaWAN message format used by the motherboard

| Index |      [0]     |     [1-47]      |
|-------|--------------|-----------------|
| Size  |       1      |   3 up to 47    |
|-------|--------------|-----------------|
| Value | message type | message payload |

**Supported message types:
1. Status message: message type 'S'
2. Immediate data: message type 'I'
3. Accumulated data: message type 'A'