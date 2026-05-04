---
title: API
---

# Hattie Camera Node API

This page defines the canonical API for the Hattie camera subsystem in the team daisy-chain architecture.

Node ID: `H`
Role: Camera / Sensors

---

## Packet Structure

All nodes on the daisy-chain share a fixed 64-byte packet format over UART at 9600 baud, 8N1.

| Byte(s) | Field | Value / Description |
|---------|-------|---------------------|
| 0–1 | Prefix | Always `AZ` (0x41 0x5A) — marks start of frame |
| 2 | Source ID | Single ASCII character identifying the sending node |
| 3 | Destination ID | Single ASCII character identifying the target node |
| 4–61 | Message | UTF-8 string payload, null-padded to fill remaining space |
| 62–63 | Suffix | Always `BY` (0x42 0x59) — marks end of frame |

**UART Configuration:** UART2, pins TX=43 / RX=44, 9600 baud, 8 data bits, no parity, 1 stop bit.

---

## Node Addressing

| Node | ID | Role |
|------|----|------|
| Rylee | `W` | Controller |
| Bryce | `B` | Motor |
| **Hattie** | **`H`** | **Camera / Sensors** |
| Riley | `F` | Sensor |
| Tim | `T` | Motor |
| Everyone (Broadcast) | `X` | All nodes |

---

## Node Responsibilities

- Receive packets addressed to `H` and process them.
- Acknowledge any packet addressed directly to `H` by replying with `ACK` to the sender.
- Forward packets addressed to other nodes unchanged.
- Forward broadcast packets (`X`) to the next node in the chain.
- Drop packets from unknown senders or looped-back own messages.
- Toggle onboard LED on Pin 2 when a packet addressed to this node is received.

---

## Messages Sent by Hattie (`H`)

| Byte | Field | Value | Description |
|------|-------|-------|-------------|
| 0–1 | Prefix | `AZ` | Frame start |
| 2 | Source | `H` | Sender is Hattie |
| 3 | Destination | Varies | ID of node being acknowledged |
| 4–6 | Message | `ACK` | Acknowledgment of received packet |
| 7–61 | Padding | `0x00` | Null bytes to fill frame |
| 62–63 | Suffix | `BY` | Frame end |

**Example packet string:** `AZHWACKby` → Hattie acknowledging a message from Rylee (W).

---

## Messages Received by Hattie (`H`)

Hattie accepts any valid 64-byte packet where destination byte = `H` or `X`.

| Source | Destination | Expected Message | Hattie's Response |
|--------|-------------|-----------------|-------------------|
| Any known node | `H` | Any string payload | Turns on LED, prints content, sends `ACK` back to sender |
| Any known node | `X` | Any broadcast string | Prints broadcast, forwards packet to next node |
| Any known node | Other node ID | Any string payload | Forwards packet unchanged, no ACK |
| Unknown node | Any | Any | Discards packet, prints error |
| `H` (self) | Any | Any | Discards packet (loop prevention) |

---

## Routing Rules

| Condition | Action |
|-----------|--------|
| `dst == H` | Process message, send ACK, turn on LED |
| `dst == X` | Print broadcast content, forward packet |
| `dst` is another known node | Forward packet unchanged |
| `src` is unknown | Discard, print error |
| `src == H` (own message looped back) | Discard silently |
| Malformed packet (bad prefix/suffix) | Discard, print error |
| Buffer overflow (> 128 bytes) | Clear buffer, print error |

---

## Error Handling

| Error | Cause | Behavior |
|-------|-------|----------|
| `ERROR: Malformed packet — discarded` | Prefix or suffix bytes do not match `AZ`/`BY` | Packet dropped |
| `ERROR: Unknown sender — discarded` | Source byte not in known ID set | Packet dropped |
| `Dropped own message (loop prevention)` | Source byte matches `H` | Packet dropped silently |
| `ERROR: Buffer overflow — cleared` | Accumulated buffer exceeds 128 bytes without a valid frame | Buffer reset |
