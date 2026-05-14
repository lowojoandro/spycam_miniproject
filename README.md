# ESP32-S3 Spy Camera PCB

This mini project is a custom PCB for a battery powered recording camera using an ESP32-S3. 


## Main Requirements

- Camera recording support
- Minimum 480p at 30 FPS
- microSD card storage
- eMMC support
- Start/stop recording button
- Target BOM cost under $25
- Must pass ERC and DRC in KiCad

## Current Design 

- Power input: USB-C
- Battery: Single cell LiPo
- Charger: LiPo charging IC
- Regulator: 3.3 V LDO
- MCU: ESP32-S3-WROOM-1
- Camera: OV2640 camera module (ribbon connected)
- Storage: microSD, optional eMMC footprint
- User controls: reset, boot, start/stop recording


---


## 3. Block Diagram

<img width="1261" height="888" alt="image" src="https://github.com/user-attachments/assets/8dd7ad94-7d2d-44f0-be11-53f7d763d030" />


This block diagram represents the major systems of this PCB. The power comes in as 5v into USB-C, which goes into a LiPo battery charging module. At that point, voltage drops to around a nominal value of 3.7V because of the MCP. This circuit is one way and therefore USB-C only charges the battery, not powering the ESP. The LiPo battery is rated to output around ___V, and is then passed through a 3.3V voltage regulator. I used the MAX604 LPO, which I'll explain later. The ESP32-S3-WROOM1 is the main controller which will operate fine from ~2.9-3.3V at __mA. 

This PCB has two means of storage: A MicroSD, or eMMC. To keep the SD card separate from the BOM, I just used a MicroSD card detector. To keep the eMMC separate from the BOM, I used a custom eMMC footprint that I found off SnapMagic.

For the camera module, I went with the OV2640 because it was the easiest camera to work with. It operatres fine under ___ which is what we expect to be at. The camera also supports 800×600 at 30 FPS, which is already much better than the requirements. 

Finally, we have three push switches for start/stop recording, boot, and reset.


---

## 4. Schematic Design



The schematic is divided into several major sections: power, ESP32-S3, camera interface, storage, and user controls. The power section includes USB-C input, LiPo charging, and 3.3 V regulation. The ESP32-S3 section contains the main microcontroller module and its required support connections. The camera section connects the OV2640 ribbon camera module to the ESP32-S3. The storage section includes both microSD and optional eMMC support.





The full KiCad schematic files can be found here:

```text
hardware/kicad/
