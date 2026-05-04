---
title: Module's Selected Major Components
---

## Module's Selected Major Components

The following sections are the selected major components necessary for the camera system for Meg.

---

## Final Component Summary

| Component | Part Number | Manufacturer | Purpose |
|-----------|-------------|--------------|---------|
| ESP32-CAM | ESP32-CAM WiFi BT BLE | AI-Thinker / Canaduino | OV2640 camera |
| 3.3V Switching Regulator | LM2575D2T-3.3R4G | onsemi | Logic power rail for ESP32 |
| 2.8V Switching Regulator | LM2575D2T-ADJG | onsemi | Camera sensor analog supply (AVDD) |
| 1.2V Switching Regulator | LM2575D2T-ADJG | onsemi | Camera core digital supply (DVDD) |
| Wall Power Supply | GST25A12-P1J | Mean Well | 9V DC 2.08A main input supply |

---

## Power Management

### 3.3V Voltage Regulator

| Name | Manufacturer | Pros | Cons | Price (1 unit) | Datasheet |
|------|--------------|------|------|----------------|-----------|
| **LM2575D2T-3.3R4G** ✓ | onsemi | Reliable, simple design, supports up to 1A output current, wide input voltage range | Larger package and lower efficiency compared to newer regulators | $2.49 | [Datasheet](https://www.onsemi.com/pdf/datasheet/lm2575-d.pdf) |
| TPS62162DSGR | Texas Instruments | Very high efficiency (95%), compact size, low heat generation | Smaller package makes PCB layout more difficult | $1.85 | [Datasheet](https://www.ti.com/lit/ds/symlink/tps62162.pdf) |
| MIC5504-3.3YM5 | Microchip Technology | Low noise output, good for sensitive camera sensors, small footprint | Only supports ~300mA output current | $0.65 | [Datasheet](https://ww1.microchip.com/downloads/en/DeviceDoc/MIC5504-Data-Sheet-DS20005810A.pdf) |

The LM2575D2T-3.3R4G was selected for its simple, proven design and compatibility with the 9V input from the Mean Well supply. Its fixed 3.3V output directly powers the ESP32 logic rail without requiring external resistor tuning, reducing design risk.

---

### 2.8V Voltage Regulator

| Name | Manufacturer | Pros | Cons | Price (1 unit) | Datasheet |
|------|--------------|------|------|----------------|-----------|
| **LM2575D2T-ADJG** ✓ | onsemi | Same footprint as 3.3V rail regulator — reuses existing schematic symbol and layout, output set by two resistors to exactly 2.8V, 1A output, wide 4V–40V input range | Larger TO-263 package compared to newer compact alternatives; lower switching frequency (52 kHz) means larger external inductor | $2.49 | [Datasheet](https://www.onsemi.com/download/data-sheet/pdf/lm2575-d.pdf) |
| TPS62162DSGR | Texas Instruments | Very high efficiency (~95%), compact 8-WSON package, 3MHz switching frequency allows tiny inductor | Minimum input voltage of 3V — tighter margin from 9V rail; smaller package increases PCB layout difficulty | $1.85 | [Datasheet](https://www.ti.com/lit/ds/symlink/tps62162.pdf) |
| AP2112K-2.8TRG1 | Diodes Inc. | Ultra-small SOT-25 footprint, very low noise — ideal for analog camera rails | LDO, not switching — drops (9V − 2.8V) × I as heat; not practical at 1A from 9V input | $0.42 | [Datasheet](https://www.diodes.com/assets/Datasheets/AP2112.pdf) |

The LM2575D2T-ADJG was selected because it shares the exact same package, schematic symbol, and BOM family as the 3.3V regulator already on the board (LM2575D2T-3.3R4G). Setting the output to 2.8V requires only two external resistors per the datasheet voltage divider formula, and reusing one regulator family across three rails reduces design risk, simplifies layout, and streamlines assembly.

---

### 1.2V Voltage Regulator

| Name | Manufacturer | Pros | Cons | Price (1 unit) | Datasheet |
|------|--------------|------|------|----------------|-----------|
| **LM2575D2T-ADJG** ✓ | onsemi | Consistent with 3.3V and 2.8V rails — single regulator family for all three supplies; output adjustable to 1.2V via resistor divider; proven 1A capability; TO-263 is solderable by hand for rework | 52 kHz switching frequency requires a larger inductor than high-frequency alternatives; TO-263 footprint is oversized relative to the current budget of this rail | $2.49 | [Datasheet](https://www.onsemi.com/download/data-sheet/pdf/lm2575-d.pdf) |
| NCV6323FELMTW12TBG | onsemi | 2A output, compact WDFN package, 2MHz switching for small passive components | Higher complexity layout; WDFN exposed-pad requires reliable solder reflow — harder to hand rework | $1.12 | [Datasheet](https://www.onsemi.com/download/data-sheet/pdf/ncv6323-d.pdf) |
| TPS62203DBVT | Texas Instruments | Very compact SOT-23-5, purpose-built for low-voltage low-current core rails, high efficiency | 300mA maximum output — marginal for camera core under full load; fixed 0.6V reference requires precise resistor values | $0.95 | [Datasheet](https://www.ti.com/lit/ds/symlink/tps62203.pdf) |

The LM2575D2T-ADJG was again selected to maintain a single regulator family across all three power rails. While alternatives offer higher switching frequency and smaller packages, the consistency benefit — one inductor value, one feedback resistor network topology, one layout pattern — outweighs the size penalty at this board scale. The output is set to 1.2V using the standard resistor divider on the ADJ pin per the datasheet.

---

## Rover Components List

### Camera Modules

| Name | Manufacturer | Pros | Cons | Price (1 unit) | Datasheet |
|------|--------------|------|------|----------------|-----------|
| [**ESP32-CAM WiFi BT BLE**](https://www.digikey.com/en/products/detail/canaduino-/ESP32-CAM-WIFI-BT-BLE/14319859) ✓ | Canaduino / AI-Thinker | Integrated MCU + OV2640 camera + Wi-Fi in one module; eliminates separate camera IC and wireless chip | Not a pure SMD camera IC; board form factor adds height | $16.99 | [Datasheet](https://www.allelcoelec.com/productdetails/ESP32-CAM%20WiFi%20BT%20BLE.html) |
| [Seeed Camera Module 21277047](https://www.digikey.com/en/products/detail/seeed-technology-co-ltd/114993115/21277047) | Seeed Technology | Compact, CV-ready, good ecosystem support | Not pure SMD, may require adapter | $15.00 | [Datasheet](https://files.seeedstudio.com/wiki/ESP32-CAM/imgs/esp32-cam.pdf) |
| [DFRobot DFR0602](https://www.digikey.com/en/products/detail/dfrobot/DFR0602/10385116) | DFRobot | Includes OV2640 2MP, same ESP32-CAM function | Not SMD-only camera chip, board form factor | $16.95 | [Datasheet](https://www.dfrobot.com/product-1783.html) |

### Power Supplies

| Name | Manufacturer | Pros | Cons | Price (1 unit) | Datasheet |
|------|--------------|------|------|----------------|-----------|
| [Tri-Mag L6R24-120](https://www.digikey.com/en/products/detail/tri-mag-llc/L6R24-120/7682639) | Tri-Mag LLC | 9V, 2A regulated, barrel jack ready | Basic functionality only | $10.38 | [Product Page](https://www.digikey.com/en/products/detail/tri-mag-llc/L6R24-120/7682639) |
| [SDI24-12-UD-P5-JVP](https://www.digikey.com/en/products/detail/jameco-electronics/SDI24-12-UD-P5-JVP/25966103) | Jameco Electronics | 9V AC/DC 2A, barrel jack | Bulkier wall adapter | $7.70 | [Product Page](https://www.digikey.com/en/products/detail/jameco-electronics/SDI24-12-UD-P5-JVP/25966103) |
| [Delta MDS-030AAC12-AB](https://www.digikey.com/en/products/detail/delta-electronics/MDS-030AAC12-AB/6150232) | Delta Electronics | Reliable, 12V 2.5A | More current than needed | $12.50 | [Datasheet](https://www.delta.com.tw/product/AC-DC_Power_Supply/En/MDS-030AAC12-AB) |

---

### ESP32 Pinout Table

## OV2640 Camera Interface Pins

| GPIO | Camera Signal | Direction | Description |
|------|--------------|-----------|-------------|
| GPIO 32 | PWDN | Output | Camera power-down control |
| GPIO 0 | XCLK | Output | Master clock to camera (10 MHz) |
| GPIO 26 | SIOD (SDA) | Bidirectional | SCCB/I2C data — camera register config |
| GPIO 27 | SIOC (SCL) | Output | SCCB/I2C clock — camera register config |
| GPIO 35 | Y9 (D7) | Input | Pixel data bit 7 (MSB) |
| GPIO 34 | Y8 (D6) | Input | Pixel data bit 6 |
| GPIO 39 | Y7 (D5) | Input | Pixel data bit 5 |
| GPIO 36 | Y6 (D4) | Input | Pixel data bit 4 |
| GPIO 21 | Y5 (D3) | Input | Pixel data bit 3 |
| GPIO 19 | Y4 (D2) | Input | Pixel data bit 2 |
| GPIO 18 | Y3 (D1) | Input | Pixel data bit 1 |
| GPIO 5 | Y2 (D0) | Input | Pixel data bit 0 (LSB) |
| GPIO 25 | VSYNC | Input | Vertical sync — marks frame boundary |
| GPIO 23 | HREF | Input | Horizontal reference — marks line boundary |
| GPIO 22 | PCLK | Input | Pixel clock — latches each pixel byte |

## Communication & System Pins

| GPIO | Function | Direction | Description |
|------|----------|-----------|-------------|
| GPIO 17 | UART2 TX | Output | Serial transmit — programming and telemetry |
| GPIO 16 | UART2 RX | Input | Serial receive — programming and telemetry |
| GPIO 4 | Flash LED | Output | Onboard white flash LED (also SD card HS_DATA1) |
| GPIO 33 | Status LED | Output | Onboard red LED — active LOW |
| GPIO 0 | Boot mode | Input | LOW = flash mode; HIGH = run mode (pull-up) |
| 3.3V | Power in | — | Logic supply from LM2575D2T-3.3R4G rail |
| 5V | Power in | — | Main board supply (recommended input) |
| GND | Ground | — | Common ground |
