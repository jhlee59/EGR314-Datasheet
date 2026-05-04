---
title: Module's Block Diagram
tags:
- tag1
- tag2
---

## Overview
This block diagram shows Team 301’s camera and sensor system, powered by a 9V wall adapter regulated to 3.3 V. The whole board and two other voltage regulators are shown, as the camera requires 2.8V and 1.2V on certain pins to work. It includes a front camera connected via a ribbon cable. Using an ESP32 WiFi module to connect wirelessly to an MQTT server on a PC to display the picture taken. 

## Meets Product Requirements
The block diagram was developed by working outward from the core requirements first, then layering in stretch goals as the architecture permitted. The ESP32 was selected as the central component because it simultaneously meets two core requirements in a single chip: the surface-mount MCU requirement and the wireless communication requirement, eliminating the need for a separate radio module. From there, peripherals were deliberately assigned: I2C on GPIO 22–21 routes to the front camera because it has a low pin count and allows a second camera to share the same bus when the reverse camera stretch goal is implemented. While UART1 on GPIO 17/16 provides a clean telemetry path from the ESP32 through the upstream header to the MQTT server, enabling full data flow traceability end-to-end. The power architecture was designed top-down from the wall supply. The 9V input feeds three independent switching regulators stepping down to 3.3V for ESP32 logic, 2.7V for the camera sensor rail, and 1.3V for the camera core ISP rail, with separate supplies per rail preventing noise coupling that would degrade image quality. Stretch goals were handled through deliberate expandability rather than omission: GPIO46 is PWM-capable for the future servo, the I2C bus supports a second device address for a reverse camera without new pins. The MQTT server is shown as a cloud node with an explicit wireless link rather than being implied.

## Block Diagram 

<img width="417" height="485" alt="Screenshot 2026-05-04 at 3 21 52 PM" src="https://github.com/user-attachments/assets/195a2004-291a-453b-baf3-3c01f1386a99" />

[Source Temptate](https://embedded-systems-design.bitbucket.io/314/team-assignments/block-diagram-protocol-and-message-structure/314-spring-2025-block%20diagram-data.drawio)
