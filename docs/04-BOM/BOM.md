---
title: Module Bill of Materials
tags:
- tag1
- tag2
---

## Overview
This module is an ESP32-S3-WROOM-1-N4 based camera board featuring an OV2640 2MP image sensor interfaced via a 24-pin FPC connector. Three LM2575 buck regulators providing regulated 3.3V, 2.8V (OV2640 AVDD), and 1.2V (OV2640 DVDD) power rails from a 12V input. The board exposes USB, a barrel jack, and a ribbon cable connector for power and communication.

## Bill of Materials

| Part Name/Description | Qty | Unit Cost | Total Cost | Manufacturer | Manufacturer # | Vendor Link | Datasheet Link | Ref Des |
|---|---|---|---|---|---|---|---|---|
| ESP32-S3-WROOM-1-N4, WiFi/BT Module, SMD | 1 | $4.40 | $4.40 | Espressif | ESP32-S3-WROOM-1-N4 | [DigiKey](https://www.digikey.com) | [Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-s3-wroom-1_wroom-1u_datasheet_en.pdf) | U1 |
| LM2575D2T-3.3R4G, 3.3V Buck Regulator, D2PAK-5 | 1 | $2.16 | $2.16 | onsemi | LM2575D2T-3.3R4G | [DigiKey](https://www.digikey.com/en/products/detail/onsemi/LM2575D2T-3-3R4G/1476688) | [Datasheet](https://www.onsemi.com/pdf/datasheet/lm2575-d.pdf) | U3 |
| LM2575D2T-ADJG, Adjustable Buck Regulator, D2PAK-5 | 2 | $2.16 | $4.32 | onsemi | LM2575D2T-ADJG | [DigiKey](https://www.digikey.com/en/products/detail/on-semiconductor/LM2575D2T-ADJG/1476693) | [Datasheet](https://www.onsemi.com/pdf/datasheet/lm2575-d.pdf) | U4, U5 |
| ESP32-CAM WiFi+BT SoC 2MP Camera | 1 | $16.99 | $16.99 | UNIVERSAL-SOLDER Electronics Ltd | ESP32-CAM-WIFI-BT-BLE | [DigiKey](https://www.digikey.com/en/products/detail/canaduino-/ESP32-CAM-WIFI-BT-BLE/14319859) | [Datasheet](https://www.allelcoelec.com/productdetails/ESP32-CAM%20WiFi%20BT%20BLE.html) | CAM |
| MECCANIXITY FFC/FPC Connector Board 24-Pin, 0.5mm to 2.54mm Adapter | 1 | $9.49 | $9.49 | MECCANIXITY | mea240220ee000628 | [Amazon](https://www.amazon.com/dp/B0CZ94PGVC) | n/a | X1 |
| SML-D12U8WT86, Red LED Diffused, 0603 SMD | 1 | $0.19 | $0.19 | Rohm Semiconductor | SML-D12U8WT86 | [DigiKey](https://www.digikey.com) | [Datasheet](https://www.rohm.com/datasheet/SML-D12U8WT86) | D6 |
| SWT0315-065025GSA, Tactile Switch SPST-NO 6x6mm SMD | 3 | $0.17 | $0.51 | GCT | SWT0315-065025GSA | [DigiKey](https://www.digikey.com) | [Datasheet](https://gct.co/files/drawings/swt0315.pdf) | SW1, SW2, SW3 |
| AIUR-06-221K, 220µH Unshielded Inductor, Radial TH | 3 | $0.87 | $2.61 | Abracon | AIUR-06-221K | [DigiKey](https://www.digikey.com) | [Datasheet](https://abracon.com/Magnetics/AIUR-06.pdf) | L1, L2, L3 |
| SS14, Schottky Diode 40V 1A, SMA | 4 | $0.23 | $0.92 | Taiwan Semiconductor | SS14 | [DigiKey](https://www.digikey.com) | [Datasheet](https://www.taiwansemi.com/assets/uploads/datasheet/SS14_A1912.pdf) | D1, D3, D4, D5 |
| EEE-FC1A101AP, 100µF 10V Electrolytic, SMD | 3 | $0.76 | $2.28 | Panasonic | EEE-FC1A101AP | [DigiKey](https://www.digikey.com) | [Datasheet](https://industrial.panasonic.com/cdbs/www-data/pdf/RDE0000/ABA0000C1215.pdf) | C1, C6, C8 |
| EEE-FK1A331P, 330µF 10V Electrolytic, SMD | 3 | $0.85 | $2.55 | Panasonic | EEE-FK1A331P | [DigiKey](https://www.digikey.com) | [Datasheet](https://industrial.panasonic.com/cdbs/www-data/pdf/RDE0000/ABA0000C1215.pdf) | C2, C7, C9 |
| CC0402KRX7R6BB104, 100nF 10V X7R Ceramic, 0402 | 5 | $0.03 | $0.15 | Yageo | CC0402KRX7R6BB104 | [DigiKey](https://www.digikey.com) | [Datasheet](https://www.yageo.com/upload/media/product/productsearch/datasheet/mlcc/UPY-GPHC_X7R_6.3V-to-50V_26.pdf) | C3, C4, C5, C10, C11 |
| RC0402JR-074K7L, 4.7kΩ 5% 0402 Resistor | 3 | $0.003 | $0.009 | Yageo | RC0402JR-074K7L | [DigiKey](https://www.digikey.com) | [Datasheet](https://www.yageo.com/upload/media/product/productsearch/datasheet/rchip/PYu-RC_Group_51_RoHS_L_12.pdf) | R3, R4, R7 |
| RC0402JR-0710KL, 10kΩ 5% 0402 Resistor | 1 | $0.006 | $0.006 | Yageo | RC0402JR-0710KL | [DigiKey](https://www.digikey.com) | [Datasheet](https://www.yageo.com/upload/media/product/productsearch/datasheet/rchip/PYu-RC_Group_51_RoHS_L_12.pdf) | R6 |
| RC0402FR-071K27L, 1.27kΩ 1% 0402 Resistor | 1 | $0.004 | $0.004 | Yageo | RC0402FR-071K27L | [DigiKey](https://www.digikey.com) | [Datasheet](https://www.yageo.com/upload/media/product/productsearch/datasheet/rchip/PYu-RC_Group_51_RoHS_L_12.pdf) | R1 |
| RC0402JR-071KL, 1kΩ 5% 0402 Resistor | 1 | $0.006 | $0.006 | Yageo | RC0402JR-071KL | [DigiKey](https://www.digikey.com) | [Datasheet](https://www.yageo.com/upload/media/product/productsearch/datasheet/rchip/PYu-RC_Group_51_RoHS_L_12.pdf) | R2 |
| BK1-S500-2-R, Fuse 5x20mm 2A | 1 | $0.36 | $0.36 | Eaton | BK1-S500-2-R | [DigiKey](https://www.digikey.com) | n/a | F1 |
| USB3131-30-0230-A, Micro-B USB 2.0 Receptacle, 5-pos TH Vertical | 1 | n/a | n/a | GCT | USB3131-30-0230-A | [DigiKey](https://www.digikey.com) | n/a | J3 |
| PJ-102AH, Barrel Jack 2.0mm ID 5.5mm OD, Horizontal TH | 1 | n/a | n/a | Same Sky (CUI) | PJ-102AH | [DigiKey](https://www.digikey.com) | n/a | J4 |
| A-08-LC-TT, 8-Pin DIP IC Socket, TH | 2 | $0.13 | $0.26 | Assmann WSW | A-08-LC-TT | [DigiKey](https://www.digikey.com) | n/a | J1, J2 |
| Single Pin Header, 2.54mm, TH | 8 | n/a | n/a | n/a | n/a | PRLTA 109 | n/a | J5, J6, J7, J8, J9, J12, J13, J14 |
| Jumper 2-pin, 2.54mm, Through Hole | 3 | n/a | n/a | n/a | n/a | PRLTA 109 | n/a | JP1, JP2, JP3 |
| Test Point, Through Hole | 34 | n/a | n/a | n/a | n/a | PRLTA 109 | n/a | TP1-TP35 |

**Estimated Total (DigiKey + Amazon): ~$47.00**
