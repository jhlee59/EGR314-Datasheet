---
title: Module's Requirements
---

## Module Requirements
The following sections document the requirements that the camera system and charging station must fulfill to support the overall rover system. Each requirement specifies what the module must do, including functional performance thresholds, target performance, and whether it is a stretch goal. For example, the front camera must detect nearby objects with clear visual feedback (not a stretch goal). The reverse camera must show the rear view when reversing (stretch goal). The charging interface must reach the docking station and ideally start charging automatically (stretch goal).

| Requirement Description | Measure of Threshold | Target Measure | Stretch Requirement (Y-N) |
|-------------------------|--------------------|----------------|--------------------------|
| Front Seeing Camera | Camera module shows nearby objects; provides clear visual feedback for operator | Detects objects at a good range for navigation | N |
| Distance Sensor | Ultrasonic or emitter/detector sensor; detects obstacles before collision | Detects objects in close proximity and triggers a sound alert | Y |
| Servo (Camera Pan/Tilt) | Hobby servo controlled via PWM; rotates at least 360° | Moves camera to any required angle for full coverage | Y |
| Reverse Camera | Camera module active when reversing; provides rear view | Integrates with controller for operator awareness | Y |
| Charging Station | Rover can sit in docking station| Rover can charge without much user input | Y |
| Surface Mounted 3.3V Switching Power Regulator | 3.2V| 3.3V | N |
| Surface Mounted Microcontroller | 1 PIC or ESP| 8-bit PIC | N |
| Wireless Communication | Able to send/receive data | Send and receive Wi-Fi Data to MQTT | Y |
