---
title: Module's Selected Major Components
---

## Module's Selected Major Components

The following sections are the selected major components necessary for the camera system and controller view from the Meg. 

Removal is TBD
### Power Management 

(**remove this note/placeholder**: this is where your 3.3 volt switching regulator, any other needed power regulator, and power source {if applicable} **THAT WERE SELECTED**)

For more details, review the ["Appendix - Component Selection Process - Power Mangement"](https://embedded-systems-design.github.io/EGR314DataSheetTemplate/Appendix/01-Componet-Selection/Component-Selection-Process/#power-management) selection.

### Sensor

(**remove this note/placeholder**: if applicable, this is where your  **SELECTED** sensor is shown. Otherwise, remove this section.)

For more details, review the ["Appendix - Component Selection Process - Sensor"](https://embedded-systems-design.github.io/EGR314DataSheetTemplate/Appendix/01-Componet-Selection/Component-Selection-Process/#sensor) selection.

### Actuator

(**remove this note/placeholder**: if applicable, this is where your **Selected** the actuator items go, which includes both the driver and motor. Otherwise, remove this section.)

For more details, review the ["Appendix - Component Selection Process - Actuator"](https://embedded-systems-design.github.io/EGR314DataSheetTemplate/Appendix/01-Componet-Selection/Component-Selection-Process/#actuator) selection.

-----------

# Rover Components List

## Camera Modules

| Name | Manufacturer | Pros | Cons | Price (1 unit) | Datasheet |
| --- | --- | --- | --- | --- | --- |
| [ESP32‑CAM WiFi BT BLE](https://www.digikey.com/en/products/detail/canaduino-/ESP32-CAM-WIFI-BT-BLE/14319859) | Canaduino / AI‑Thinker | Integrated MCU + camera, easy ESP32 integration | Not pure camera IC, board adds size | $16.99 | [Datasheet](https://www.allelcoelec.com/productdetails/ESP32-CAM%20WiFi%20BT%20BLE.html) |
| [Seeed Camera Module 21277047](https://www.digikey.com/en/products/detail/seeed-technology-co-ltd/114993115/21277047) | Seeed Technology | Compact, CV-ready, good ecosystem support | Not pure SMD, may require adapter | $15.00 | [Datasheet](https://files.seeedstudio.com/wiki/ESP32-CAM/imgs/esp32-cam.pdf) |
| [DFRobot DFR0602](https://www.digikey.com/en/products/detail/dfrobot/DFR0602/10385116) | DFRobot | Includes OV2640 2MP, same ESP32‑CAM function | Not SMD-only camera chip, board form factor | $16.95 | [Datasheet](https://www.dfrobot.com/product-1783.html) |

## Distance Sensors

| Name | Manufacturer | Pros | Cons | Price (1 unit) | Datasheet |
| --- | --- | --- | --- | --- | --- |
| [VL53L3CXV0DH‑1](https://www.digikey.com/en/products/detail/stmicroelectronics/VL53L3CXV0DH-1/11658314) | STMicroelectronics | SMT, I²C range ~3.1 m, good accuracy | Needs breakout/supporting components | $4.95 | [Datasheet](https://www.st.com/resource/en/datasheet/vl53l3cx.pdf) |
| [VL53L8CXV0GC‑1](https://www.digikey.com/en/products/detail/stmicroelectronics/VL53L8CXV0GC-1/18085238) | STMicroelectronics | Multizone ToF, long range ~4 m | More complex interface than simple sensor | $7.63 | [Datasheet](https://www.st.com/resource/en/datasheet/vl53l8cx.pdf) |
| [GP2Y0A41SK0F](https://www.digikey.com/en/products/detail/sharp-socle-technology/GP2Y0A41SK0F/3884447) | Sharp | Analog distance 4–30 cm, simple interface | Not SMD, needs ADC | $8.18 | [Datasheet](https://global.sharp/products/device/lineup/data/pdf/datasheet/gp2y0a41sk_e.pdf) |

## Motion / Proximity Sensors

| Name | Manufacturer | Pros | Cons | Price (1 unit) | Datasheet |
| --- | --- | --- | --- | --- | --- |
| [VCNT2020](https://www.digikey.com/en/products/detail/vishay-semiconductor-opto-division/VCNT2020/7560297) | Vishay | Small SMD reflective opto, fast response | Very short sensing range (~2–7 mm) | $0.56 | [Datasheet](https://www.vishay.com/docs/80362/vcnt2020.pdf) |
| [GP2S60B](https://www.digikey.com/en/products/detail/sharp-socle-technology/GP2S60B/857215) | Sharp | SMD reflective sensor, surface-mount | Short range, only simple analog/digital output | $0.75 | [Datasheet](https://global.sharp/products/device/lineup/data/pdf/datasheet/gp2s60_e.pdf) |
| [GP2S60](https://www.digikey.com/en/products/detail/sharp-socle-technology/GP2S60/457882) | Sharp | SMT, detects reflective presence | Tiny range, no distance data | $0.70 | [Datasheet](https://global.sharp/products/device/lineup/data/pdf/datasheet/gp2s60_e.pdf) |

## Servo

| Name | Manufacturer | Pros | Cons | Price (1 unit) | Datasheet |
| --- | --- | --- | --- | --- | --- |
| [Adafruit 360° Continuous Servo (154)](https://www.digikey.com/en/products/detail/adafruit-industries-llc/154/5774222) | Adafruit | Continuous rotation, good quality | Uses 5 V supply | $11.95 | [Product Page](https://www.adafruit.com/product/154) |
| [Pololu 2820 Continuous Servo](https://www.digikey.com/en/products/detail/pololu/2820/10450037) | Pololu | Hobby-grade continuous, decent torque | Requires external driver for heavy load | $14.95 | [Product Page](https://www.pololu.com/product/2820) |
| [DFRobot SER0039](https://www.digikey.com/en/products/detail/dfrobot/SER0039/7087152) | DFRobot | Good for rover control, widely available | Quality varies | $12.50 | [Product Page](https://www.dfrobot.com/product-1407.html) |

## Power Supplies 

| Name | Manufacturer | Pros | Cons | Price (1 unit) | Datasheet |
| --- | --- | --- | --- | --- | --- |
| [Tri‑Mag L6R24‑120](https://www.digikey.com/en/products/detail/tri-mag-llc/L6R24-120/7682639) | Tri‑Mag LLC | 12 V, 2 A regulated, barrel jack ready | Basic functionality only | $10.38 | [Product Page](https://www.digikey.com/en/products/detail/tri-mag-llc/L6R24-120/7682639) |
| [SDI24‑12‑UD‑P5‑JVP](https://www.digikey.com/en/products/detail/jameco-electronics/SDI24-12-UD-P5-JVP/25966103) | Jameco Electronics | 12 V AC/DC 2 A, barrel jack | Bulkier wall adapter | $7.70 | [Product Page](https://www.digikey.com/en/products/detail/jameco-electronics/SDI24-12-UD-P5-JVP/25966103) |
| [Delta MDS‑030AAC12‑AB](https://www.digikey.com/en/products/detail/delta-electronics/MDS-030AAC12-AB/6150232) | Delta Electronics | Reliable, 12 V 2.5 A | More current than needed | $12.50 | [Datasheet](https://www.delta.com.tw/product/AC-DC_Power_Supply/En/MDS-030AAC12-AB) |
