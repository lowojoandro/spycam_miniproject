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

### Main Design Blocks

| Block | Component / Method | Purpose |
|---|---|---|
| Power Input | USB-C | Provides charging input |
| Battery | Single-cell LiPo | Powers the device |
| Charger | LiPo charging IC | Charges the battery from USB-C |
| Regulator | 3.3 V LDO | Powers ESP32, camera, and storage |
| MCU | ESP32-S3-WROOM-1 | Main controller |
| Camera | OV2640 ribbon camera module | Captures video |
| Storage | microSD + optional eMMC | Saves video data |
| Controls | Reset, boot, start/stop button | User control and programming |

---


## 3. Block Diagram

![Block Diagram](hardware/images/block_diagram.png)

The block diagram shows the major subsystems of the camera PCB. The ESP32-S3 acts as the central controller. It receives image data from the OV2640 camera module, manages storage through the microSD card and optional eMMC footprint, and handles user inputs such as reset, boot, and start/stop recording. Power is supplied from a LiPo battery, with USB-C used for charging.


---

## 4. Schematic Design

![Schematic Preview](hardware/images/schematic_preview.png)

The schematic is divided into several major sections: power, ESP32-S3, camera interface, storage, and user controls. The power section includes USB-C input, LiPo charging, and 3.3 V regulation. The ESP32-S3 section contains the main microcontroller module and its required support connections. The camera section connects the OV2640 ribbon camera module to the ESP32-S3. The storage section includes both microSD and optional eMMC support.

The full KiCad schematic files can be found here:

```text
hardware/kicad/
