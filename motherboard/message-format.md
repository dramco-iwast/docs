---
title: Message format
parent: Motherboard
has_toc: true
nav_order: 2
layout: default
---

LoRaWAN message format used by the motherboard

| Field | Size | Index | Description |
|-----------|--------|-------------|
| `<message-type>` | 1 byte | 0 | The Message Type field indicates what type of message has been sent. |
| `<message-payload>` | 3 up to 47 bytes | 1 up to 47 | The payload format depends on the Message Type.|
|-----------|--------|-------------|

## Supported message types:
1. Status message: message type 'S'
2. Immediate data: message type 'I'
3. Accumulated data: message type 'A'

## Status message format

| Field | Size | Index | Description / Value|
|-----------|--------|-------------|
| `<message-type>` | 1 byte | 0 | 'S' (0x53) for a status message |
| `<motherboard-id>` | 2 bytes | 1-2 | The 16-bit Motherboard ID.|
|-----------|--------|-------------|