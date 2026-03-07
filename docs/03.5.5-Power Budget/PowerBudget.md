---
title: Power Budget
---

## Section A — All Major Components

| Component | Part Number | Supply Voltage Range | # | Absolute Max Current (mA) | Total (mA) |
|---|---|---|---|---|---|
| ESP32-S3-WROOM-1-N4 | ESP32-S3-WROOM-1-N4 | +3.0–3.6V | 1 | 500 | 500 |
| OV2640 Camera (DOVDD) | OV2640 | +3.3V | 1 | 40 | 40 |
| OV2640 Camera (AVDD) | OV2640 | +2.8V | 1 | 60 | 60 |
| OV2640 Camera (DVDD) | OV2640 | +1.3V | 1 | 30 | 30 |
| Debug LED (D6) | Red LED | +3.3V | 1 | 20 | 20 |

---

## Section B — Power Rails

### +3.3V Rail

| Component | Part Number | Supply Voltage Range | # | Absolute Max Current (mA) | Total (mA) |
|---|---|---|---|---|---|
| ESP32-S3-WROOM-1-N4 | ESP32-S3-WROOM-1-N4 | +3.0–3.6V | 1 | 500 | 500 |
| OV2640 DOVDD | OV2640 | +3.3V | 1 | 40 | 40 |
| Debug LED (D6) | Red LED | +3.3V | 1 | 20 | 20 |
| **Subtotal** | | | | | **560 mA** |
| **25% Safety Margin** | | | | | **+140 mA** |
| **Total Required on +3.3V Rail** | | | | | **700 mA** |

### +2.8V Rail

| Component | Part Number | Supply Voltage Range | # | Absolute Max Current (mA) | Total (mA) |
|---|---|---|---|---|---|
| OV2640 AVDD | OV2640 | +2.5–3.0V | 1 | 60 | 60 |
| **Subtotal** | | | | | **60 mA** |
| **25% Safety Margin** | | | | | **+15 mA** |
| **Total Required on +2.8V Rail** | | | | | **75 mA** |

### +1.3V Rail

| Component | Part Number | Supply Voltage Range | # | Absolute Max Current (mA) | Total (mA) |
|---|---|---|---|---|---|
| OV2640 DVDD | OV2640 | +1.1–1.5V | 1 | 30 | 30 |
| **Subtotal** | | | | | **30 mA** |
| **25% Safety Margin** | | | | | **+8 mA** |
| **Total Required on +1.3V Rail** | | | | | **38 mA** |

---

## Section C — Regulator Selection

### +3.3V — U3

| | Option 1 | Option 2 | Final Choice |
|---|---|---|---|
| **Part** | LM2575D2T-3.3R4G | AMS1117-3.3 (LDO) | **LM2575D2T-3.3R4G** |
| **Type** | Buck (switching) | LDO (linear) | |
| **Max Output** | 1000 mA | 800 mA | |
| **Efficiency** | ~77% | ~27% (12V→3.3V) | |
| **Pros** | High efficiency, handles 700 mA easily, low heat | Simple circuit, few external parts | |
| **Cons** | Requires inductor + Schottky diode | Drops 8.7V as heat — ~6W dissipation at 700 mA, requires heatsink | |
| **Rationale** | Dropping 12V→3.3V with a linear regulator at 700 mA = **6W of heat**. Buck regulator is required. | | |

**Regulator or Source Choice:** U3 — LM2575D2T-3.3R4G | [DigiKey](https://www.digikey.com/en/products/detail/onsemi/LM2575D2T-3-3R4G/1476688)
**Total Remaining Current Available on +3.3V Rail:** 1000 − 700 = **300 mA**

---

### +2.8V — U4

| | Option 1 | Option 2 | Final Choice |
|---|---|---|---|
| **Part** | LM2575D2T-ADJG | MCP1826-2.8 (LDO) | **LM2575D2T-ADJG** |
| **Type** | Buck (switching) | LDO (linear) | |
| **Max Output** | 1000 mA | 1000 mA | |
| **Pros** | Same footprint as U3, high efficiency, already in BOM | Simple design, few external parts | |
| **Cons** | Requires feedback resistors R_top/R_bot | Inconsistent with rest of design, adds unique part to BOM | |
| **Rationale** | Design consistency — same part as U5, already in BOM, no added cost or new footprint. | | |

**Regulator or Source Choice:** U4 — LM2575D2T-ADJG | [DigiKey](https://www.digikey.com/en/products/detail/on-semiconductor/LM2575D2T-ADJG/1476693)
**Total Remaining Current Available on +2.8V Rail:** 1000 − 75 = **925 mA**

---

### +1.3V — U5

| | Option 1 | Option 2 | Final Choice |
|---|---|---|---|
| **Part** | LM2575D2T-ADJG | TPS62082 (sync buck) | **LM2575D2T-ADJG** |
| **Type** | Buck (switching) | Synchronous buck | |
| **Max Output** | 1000 mA | 2000 mA | |
| **Pros** | Already in BOM, same footprint as U4, proven design | Higher efficiency, smaller inductor needed | |
| **Cons** | Slight overkill for 38 mA load | New part, new footprint, higher cost, unnecessary complexity | |
| **Rationale** | Load is only 38 mA — overkill is acceptable. Reusing the same part as U4 eliminates a unique component from the BOM. | | |

**Regulator or Source Choice:** U5 — LM2575D2T-ADJG | [DigiKey](https://www.digikey.com/en/products/detail/on-semiconductor/LM2575D2T-ADJG/1476693)
**Total Remaining Current Available on +1.3V Rail:** 1000 − 38 = **962 mA**

---

## Section D — External Power Source

### Power Source 1 — Barrel Jack Wall Supply (J4)

| Component | Part | Input | Output Voltage | Max Current (mA) | Unit |
|---|---|---|---|---|---|
| Wall Supply | J4 (12V DC barrel jack) | 110VAC | +12V | 2000 | mA |

| Power Rails Connected to Source 1 | Regulator | Current Required (mA) |
|---|---|---|
| +3.3V Rail | U3 — LM2575D2T-3.3R4G | 700 |
| +2.8V Rail | U4 — LM2575D2T-ADJG | 75 |
| +1.3V Rail | U5 — LM2575D2T-ADJG | 38 |
| **Total Required** | | **813 mA** |
| **Total Available** | | **2000 mA** |
| **Total Remaining** | | **1187 mA** |


---

## Section E — Battery Life

This design uses a **wall supply only**. No battery is used in normal operation.

**Battery life calculation: N/A**
