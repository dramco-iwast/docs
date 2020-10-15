---
title: Message format
parent: Motherboard
has_toc: true
nav_order: 2
layout: default
---

LoRaWAN message format used by the motherboard

|-:|:-:|:-:|
|__Index__ |      [0]     |     [1-47]      |
|__Size__  |       1      |   3 up to 47    |
|__Value__ | message type | message payload |

## Supported message types:
1. Status message: message type 'S'
2. Immediate data: message type 'I'
3. Accumulated data: message type 'A'

## Status message format

|-:|:-:|:-:|
|__Index__ |  [0] | [1-2]  | [3] | [4] | [5-8] |
|__Size__  |  1   |   2    | 1   | 1   | 4     |
|__Value__ | 'S'  | motherboard id | data accumulation enabled | nr of sensors | local epoch |