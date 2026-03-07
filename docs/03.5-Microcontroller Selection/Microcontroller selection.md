---
title: Microcontroller Selection
---
ESP32-S3-WROOM-1-N4

Note: Work in Process, but half complete

## Project-Specific Requirements

| Requirement | Detail |
|---|---|
| Camera interface | Parallel DVP — 8 data lines + PCLK, VSYNC, HREF, XCLK = 11 GPIO |
| I2C (SCCB) | SDA + SCL for OV2640 config = 2 GPIO |
| UART | TX + RX for teammate communication = 2 GPIO |
| USB | D+ / D- for programming = 2 pins (IO19, IO20) |
| GPIO | Debug LED, debug button, boot button, EN reset = 4 GPIO |
| **Total GPIO needed** | **21 pins** |

## ESP32-S3-WROOM-1-N4 Resources

| Resource | Available | Needed | Status |
|---|---|---|---|
| GPIO | 45 | 21 | Exceeds requirements |
| I2C controllers | 2 | 1 | Exceeds requirements |
| UART controllers | 3 | 1 | Exceeds requirements |
| USB OTG (native) | 1 | 1 | Meets requirements |
| Camera DVP interface | 1 (hardware) | 1 | Meets requirements |
| Flash | 4MB | ~2MB | Meets requirements |
| PSRAM | None | QVGA JPEG only | Meets requirements with constraints |
| WiFi | 802.11 b/g/n | 802.11 b/g/n | Meets requirements |

## Role Description

This subsystem handles camera capture and wireless image transmission for the rover.
The ESP32-S3 drives a bare OV2640 sensor over parallel DVP and configures it over I2C.
Captured JPEG frames are streamed over WiFi via HTTP MJPEG to a ground station.
UART communicates status and trigger commands to teammate subsystems.
Power responsibilities include generating +3.3V, +2.8V, and +1.3V from +12V using three

---

## Compatibility

| Concern | Finding |
|---|---|
| OV2640 + ESP32-S3 MicroPython | Supported via [cnadler86/micropython-camera-API](https://github.com/cnadler86/micropython-camera-API) |
| Parallel DVP | Hardware-accelerated via LCD_CAM peripheral — no bit-banging |
| No PSRAM | QVGA + JPEG confirmed working in cnadler86 firmware |
| SCCB vs I2C | OV2640 SCCB is I2C-compatible at 100kHz — no issues |


## Final Choice

The ESP32-S3-WROOM-1-N4 is optimal for three reasons: hardware DVP camera support via the
LCD_CAM peripheral eliminates bit-banged capture; native USB OTG on IO19/IO20 removes the
need for a separate USB-UART bridge; and integrated WiFi enables MJPEG streaming with no
external radio. At $4.40 the N4 variant covers all requirements with 20+ GPIO to spare.

**DigiKey:** [ESP32-S3-WROOM-1-N4](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639)
