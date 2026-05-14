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


## Folder Structure

- `hardware/kicad/` - KiCad schematic and PCB files
- `hardware/bom/` - Bill of materials
- `docs/` - Pinout, design notes, and documentation
- `sourcing/` - Where to source components 
- `firmware/` - Future ESP32 firmware
- `casing/solidworks/` - Casing for the Camera
