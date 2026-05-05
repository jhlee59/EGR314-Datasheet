---
title: Reflection
---

# Reflection

## Review of Module's Success

The core non-stretch requirements were successfully met. The ESP32-S3 was integrated as the surface-mount microcontroller, and the 3.3V switching power regulator (LM2575D2T-3.3R4G) met all logic rail voltage and current specifications. Wireless telemetry and MQTT connections were established using the ESP32's integrated Wi-Fi, and the front camera was fully operationalized using the OV2640 module. 

However, none of the five stretch goals—the distance sensor, servo pan/tilt, reverse camera, and automatic charging station—were completed. This was primarily due to extensive time spent resolving fundamental bring-up and camera integration issues, which served as a valuable learning experience for V2.0 designs.

---

## Microcontroller and Module Startup Tips

Reflecting on the bring-up process, the following procedures are highly recommended for future iterations:

* **Verify power rails:** Check that all voltage rails (3.3V, 2.8V, and 1.2V) are correct with a multimeter under no load before connecting the microcontroller.
* **Check USB continuity:** Verify that VBUS, D+, D−, and GND lines are properly connected before attempting to flash the device.
* **Fallback to a devkit:** If the custom board fails to flash, immediately switch to an external devkit to isolate firmware from hardware issues.
* **Pin management:** Allocate tasks properly using `xTaskCreatePinnedToCore()` to run both the camera and Wi-Fi stack concurrently.
* **Monitor strapping pins:** Ensure GPIO0 is held LOW to enter flash mode and HIGH for normal boot.
* **Stock spare components:** Keep extra USB connectors and modules on hand to avoid delays during bring-up.

---

## Lessons Learned

1. **Know when to pivot:** Troubleshooting an ambiguous hardware/firmware issue indefinitely introduces major schedule risks. Use workarounds, such as jumper wires or devkits, to maintain project momentum.
2. **Verify physical footprints:** Always cross-reference all parts against the manufacturer's mechanical drawings to avoid footprint and spacing errors.
3. **Hardware architectural limits:** The ESP32 shares resources between Wi-Fi and the camera, which requires careful task scheduling and component selection to prevent system trade-offs.
4. **Use fixed-voltage regulators:** Adjustable regulators (e.g., LM2575D2T-ADJG) add complexity; fixed-output variants are easier to work with in initial designs.
5. **Read the datasheet:** Review the mechanical, layout, and electrical specifications completely before design submission.
6. **Communicate on shared protocols:** Standardizing packet formats and baud rates early prevents integration failures.
7. **Conduct manual design reviews:** Automated DRC and ERC are helpful, but manual checks are necessary to verify that symbol pins map correctly to physical pads.
8. **Order boards early:** Sending the design to fabrication as early as possible allows time for a second spin of the board if errors occur.
9. **Refine assembly skills:** Fine-pitch SMD assembly (such as 0402 components) requires practice to prevent tombstoning and cold joints.
10. **Validate power budgets:** Calculations prevent thermal issues and guide the selection of switching versus linear regulators.

---

## Recommendations for Future Students

1. **Read datasheets thoroughly:** Most bring-up issues can be solved by following manufacturer guidelines.
2. **Order PCBs early:** A fabrication buffer allows you to focus on firmware and testing rather than waiting for parts.
3. **Validate with devkits:** Develop and test your code on a known-good platform before testing on the custom board.
4. **Learn when to pivot:** Do not let a single issue derail your entire project schedule.
5. **Double-check footprints:** Verify every footprint against the actual physical components before fabrication.
