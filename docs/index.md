---
title: Welcome
tags:
- tag1
- tag2
---
<center>
<font size= "6">Hattie Lee Datasheet</font><br>
as part of<br>
<font size= "8"> Meg the Rover </font><br>
for<br>
<font size= "5"> Team 301 </font><br>

**Submission: May, 04, 2026**
</center>

<img width="805" height="542" alt="Screenshot 2026-05-04 at 1 55 43 PM" src="https://github.com/user-attachments/assets/3d2a02f5-56d5-4719-939d-a9e3a9df4a15" />

## Introduction

This datasheet describes the design and hardware used for the camera and processing subsystem of the rover project. Its purpose is to document the components, electrical connections, and power management required for the subsystem to operate. This information allows readers to understand the design, reproduce the hardware, and integrate it with the rest of the rover system.

### Project Summary

The team project focuses on building a rover capable of wireless monitoring and visual feedback. The rover combines several subsystems, including mobility, control, power management, and imaging, to create a compact remote observation platform.

My portion of the project focuses on the camera and processing subsystem built around the ESP32-S3-WROOM-1-N4 microcontroller. This subsystem captures images from the camera and transmits them wirelessly via Wi-Fi. It includes the camera interface, processing module, and the power regulation needed to supply a stable 3.3 V rail.

More information about the full rover system can be found in the team report:[here](https://asu-egr314-301-s-2026.github.io/EGR314-Team301/)

### My Contribution

The development of the exploration rover was a collaborative team effort to create a modular, well-documented rover. Focusing specifically on the camera subsystem, we began by establishing the [project requirements](https://jhlee59.github.io/EGR314-Datasheet/01-Requirements/Requirements/) and developing [block diagrams](https://jhlee59.github.io/EGR314-Datasheet/02-Block-Diagram/Block-Diagram/). From there, I researched and evaluated the needed [components](https://jhlee59.github.io/EGR314-Datasheet/03-Component-Selection/Component-Selection/). Then, when I would use the ESP32 or PIC detailed in the[microcontroller selection](https://jhlee59.github.io/EGR314-Datasheet/03.5-Microcontroller%20Selection/Microcontroller%20selection/).  I also have a detailed [power budget](https://jhlee59.github.io/EGR314-Datasheet/03.5.5-Power%20Budget/PowerBudget/) to calculate the system while the camera was active, designed the [schematic](https://jhlee59.github.io/EGR314-Datasheet/05-Schematic/schematic/) and [PCB](https://jhlee59.github.io/EGR314-Datasheet/06-PCB/pcb/) layout for efficient power and data routing, and created a complete [Bill of Materials (BOM)](https://jhlee59.github.io/EGR314-Datasheet/04-BOM/BOM/) alongside a structured [API](https://jhlee59.github.io/EGR314-Datasheet/03.5.5.5-API/API/) to enable seamless Wi-Fi video streaming and data transmission.

Following the assembly of the prototype, we compiled all supporting [resources](https://jhlee59.github.io/EGR314-Datasheet/08-Resources/resource/) and documentation into the [appendix](https://jhlee59.github.io/EGR314-Datasheet/Appendix/) to ensure full traceability of our testing methods. Through rigorous testing, we verified the functionality of the camera to ensure it operated reliably within the cohesive system alongside the motors and humidity sensor. This development process concluded with a thorough [reflection](https://jhlee59.github.io/EGR314-Datasheet/07-Reflection/Reflection/) on our design choices and image performance metrics, providing a clear roadmap for future improvements and iterations.

