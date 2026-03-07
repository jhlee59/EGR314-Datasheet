---
title: Module's Selected Major Components
---

## Module's Selected Major Components

The following sections are the selected major components necessary for the camera system for Meg. 

### Power Management 

| Name | Manufacturer | Pros | Cons | Price (1 unit) | Datasheet |
|-----|-----|-----|-----|-----|-----|
| LM2575D2T-3.3R4G | onsemi | Reliable, simple design, supports up to 1A output current, wide input voltage range | Larger package and lower efficiency compared to newer regulators | $2.49 | [Datasheet](https://www.onsemi.com/pdf/datasheet/lm2575-d.pdf) |
| TPS62162DSGR | Texas Instruments | Very high efficiency (95%), compact size, low heat generation | Smaller package makes PCB layout more difficult | $1.85 |  [Datasheet](https://www.ti.com/lit/ds/symlink/tps62162.pdf) |
| MIC5504-3.3YM5 | Microchip Technology | Low noise output, good for sensitive camera sensors, small footprint | Only supports ~300mA output current | $0.65 |  [Datasheet](https://ww1.microchip.com/downloads/en/DeviceDoc/MIC5504-Data-Sheet-DS20005810A.pdf) |
| 18650 Lithium-Ion Battery | Various | High capacity, rechargeable, common for robotics applications | Requires protection and charging circuitry | $5.00 | [Datasheet]() |
| GST25A12-P1J 12V Adapter | Mean Well | Reliable regulated 12V output, wide input range (100–240VAC), safety certified | Requires DC barrel jack connector and wall outlet | $11–14 |  [Datasheet](https://www.meanwell-web.com/Article/DownloadAsset/GST25A-SPEC.PDF) | 

-----------

# Rover Components List

## Camera Modules

| Name | Manufacturer | Pros | Cons | Price (1 unit) | Datasheet |
| --- | --- | --- | --- | --- | --- |
| [ESP32‑CAM WiFi BT BLE](https://www.digikey.com/en/products/detail/canaduino-/ESP32-CAM-WIFI-BT-BLE/14319859) | Canaduino / AI‑Thinker | Integrated MCU + camera, easy ESP32 integration | Not pure camera IC, board adds size | $16.99 | [Datasheet](https://www.allelcoelec.com/productdetails/ESP32-CAM%20WiFi%20BT%20BLE.html) |
| [Seeed Camera Module 21277047](https://www.digikey.com/en/products/detail/seeed-technology-co-ltd/114993115/21277047) | Seeed Technology | Compact, CV-ready, good ecosystem support | Not pure SMD, may require adapter | $15.00 | [Datasheet](https://files.seeedstudio.com/wiki/ESP32-CAM/imgs/esp32-cam.pdf) |
| [DFRobot DFR0602](https://www.digikey.com/en/products/detail/dfrobot/DFR0602/10385116) | DFRobot | Includes OV2640 2MP, same ESP32‑CAM function | Not SMD-only camera chip, board form factor | $16.95 | [Datasheet](https://www.dfrobot.com/product-1783.html) |

## Power Supplies 

| Name | Manufacturer | Pros | Cons | Price (1 unit) | Datasheet |
| --- | --- | --- | --- | --- | --- |
| [Tri‑Mag L6R24‑120](https://www.digikey.com/en/products/detail/tri-mag-llc/L6R24-120/7682639) | Tri‑Mag LLC | 12 V, 2 A regulated, barrel jack ready | Basic functionality only | $10.38 | [Product Page](https://www.digikey.com/en/products/detail/tri-mag-llc/L6R24-120/7682639) |
| [SDI24‑12‑UD‑P5‑JVP](https://www.digikey.com/en/products/detail/jameco-electronics/SDI24-12-UD-P5-JVP/25966103) | Jameco Electronics | 12 V AC/DC 2 A, barrel jack | Bulkier wall adapter | $7.70 | [Product Page](https://www.digikey.com/en/products/detail/jameco-electronics/SDI24-12-UD-P5-JVP/25966103) |
| [Delta MDS‑030AAC12‑AB](https://www.digikey.com/en/products/detail/delta-electronics/MDS-030AAC12-AB/6150232) | Delta Electronics | Reliable, 12 V 2.5 A | More current than needed | $12.50 | [Datasheet](https://www.delta.com.tw/product/AC-DC_Power_Supply/En/MDS-030AAC12-AB) |
