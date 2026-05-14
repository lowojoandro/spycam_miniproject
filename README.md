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


### USB-C Power Entry


<img width="500" height="388" alt="image" src="https://github.com/user-attachments/assets/ae17c6a2-d1ae-4d19-ac5c-3ce5ce03ea7c" />


The UCB_C_Receptable part is ____. I use 5k resistors as pull down for CC1 and CC2 per the datasheet. I use a USBC connector to protect the data lines and route it to D- and D+. The diode I use has a clamping voltage of 12v, so under normal 5v operations it doesn't activate, but in cases of voltage spikes, it'll short to ground. I use 4.7uF capacitors for decoupling per the datasheet. This is a recurring value throughout the pcb. 



### LiPo Charger / Connector


<img width="521" height="555" alt="image" src="https://github.com/user-attachments/assets/8ce0ed01-6c61-4032-b262-ecc1e221afaf" />


For LiPo charger, the MCP73 is preferable because it operates at 4.2V, which gets me closer to the 3.3V when it finally reaches the LDO. Also it takes in 5v input and 400-1000mA, >500mA and 5v. I put a note on R4 because it connect to PROG, which regulates how fast you're charging. The higher the R, the slower it charges. It may be preferable to charge slower to prevent spiking. The LED is there to show charging status. Again, we have decoupling capacitors at the input V and output V. 




### Battery


<img width="480" height="448" alt="image" src="https://github.com/user-attachments/assets/e791f2d8-1fc0-43c8-8a7a-67c80b3fda71" />


The battery is a single cell LiPo battery that connects to a single pole, single throw switch for simplicity. The 25k is for protection before entering at nominal voltage 3.7V. Then, we have a MOSFET which is controlled by the SPST switch. t takes in 5v input and 400-1000mA, and is a lipo charger. So it basically meets what we need which is >500mA and 5v. 



### 3.3V LDO


<img width="500" height="340" alt="image" src="https://github.com/user-attachments/assets/bc3afa20-1aab-48d9-91b0-1a318f939aae" />


You could go a lot of different routes for the regulator. The goal is to minimize the quiescent current and also the low dropout. The TPS783xx part is commony used to deal with quiescent Current but won't be viable for this pcb. I ended up sticking with the MAX604 because although it has a droupout V of 840V at 400mA, I'll get a Vout of around 2.9-3.0V, assuming our nominal aperage is 500mA, which the ESP32 can still run on (based on reddit posts). The values for the decoupling capacitors are 10uF per the datasheet.





### ESP32-S3-WROOM-1


<img width="431" height="511" alt="image" src="https://github.com/user-attachments/assets/5f878b4a-6c12-41bf-a982-c50d45718212" />


I chose the S3-WROOM-1 bceause it has enough GPIO pins for the camera and storage connections. It also already has PSRAM and it's own crystal built so I wouldn't need to make one. Note that I dedicate a good portion of pins for the camera module so that it can run 8 bits, fulfilling the 480p 30fps requirement. This leaves very little space for the eMMC and I actually have to pin it on 4 bit mode. I can't use the other pins because they're dedicate for internal operations like booting and UART and such.



### OV2640 Camera


<img width="575" height="497" alt="image" src="https://github.com/user-attachments/assets/3f76741b-e935-428f-9739-98760a9ff699" />



This is the standard camera that most people use for ESP32 projects, but the standard Kicad library didn't have the component. So, I found it on SnapMagic.com and imported it to kicad. The link is here: https://www.snapeda.com/parts/OV2640/Omnivision%20Technologies/view-part/?ref=search&t=OV2640%20camera&ab_test_case=b

It operates at 3.3v, can output lower resolution video modes such as SVGA mode which si 800×600 at 30 FPS, which exceeds the project’s minimum 480p/30 FPS requirement. It also supports compressed output so it's less strenuous on memory. Note the pull down resistors. 



### eMMC


<img width="559" height="387" alt="image" src="https://github.com/user-attachments/assets/d7e73491-18f6-45bb-8a3d-410fb654aeda" />


Similar to the camera, kicad didn't have the component, so I used this: https://www.snapeda.com/parts/EMMC08G-MB29-PM9B/Kingston/view-part/?company=N%2FA&amp;welcome=home&amp;ref=search&amp;t=eMMC&amp;ab_test_case=b

There's multiple similar eMMCs but this one in particular seemed to be easier to source. Just as I noted in the schematic, the eMMC is on 4 bit mode because of the lack of GPIO pins. 



### MicroSD detector


<img width="694" height="392" alt="image" src="https://github.com/user-attachments/assets/6b0f0f58-ec69-4ff9-b27c-f752242620cd" />



This is just a standard MicroSD detector. The footprint used however is Molex one because it seemed to be most common. The most important thing to note here is that I didn't actually wire this component (because lack of pins), effectively prioritizing the eMMC as the storage device. If instead we wanted the SD, then I would just replace the eMMC connections with the SD detector.



### Buttons



<img width="481" height="826" alt="image" src="https://github.com/user-attachments/assets/5ae11e23-5b90-4269-a05d-b10b508a96a6" />


The top circuit is the button for the booting process. It connects to EN pin of the ESP32 and has an extra resistor to act as a pull down pin. 
The middle circuit is the button for the manual download as well as reset
The bottom circuit is start/stop button. High is start, low is stop.








