# ESP32-S3 Spy Camera PCB

This mini project is a custom PCB for a battery powered recording camera using an ESP32-S3.
The download to the files are in the hardware folder.


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

## 1. Parts Table 


### Normal Sourcing

This table lists the current PCB components, estimated prices, and target pricing for keeping the project under the $25 goal.
This is NOT using parts sourced from China specifically.

- **Current estimated total:** $43.21
- **Target estimated total:** $16.86

| Ref | Qty | Part / Value | Footprint | Unit Price | Extended | Target Extended | Source |
|---|---:|---|---|---:|---:|---:|---|
| BT1 | 1 | Battery_Cell | Battery:BatteryHolder_Keystone_103_1x20mm | $0.3600 | $0.3600 | $0.3600 |  |
| C1,C2,C4 | 3 | 4u7 | Capacitor_SMD:C_0201_0603Metric | $0.0200 | $0.0600 | $0.0600 | [LCSC](https://www.lcsc.com/category/1142.html) |
| C3,C7,C11,C14,C16 | 5 | 4.7uF | Capacitor_SMD:C_0201_0603Metric | $0.0200 | $0.1000 | $0.1000 | [LCSC](https://www.lcsc.com/category/1142.html) |
| C5,C6 | 2 | 10uF | Capacitor_SMD:C_0201_0603Metric | $0.0300 | $0.0600 | $0.0600 | [LCSC](https://www.lcsc.com/category/1142.html) |
| C8,C9,C10,C12,C13,C15,C18 | 7 | 100nF | Capacitor_SMD:C_0201_0603Metric | $0.0008 | $0.0056 | $0.0056 | [LCSC](https://www.lcsc.com/product-detail/C284966.html) |
| CAM1 | 1 | OV2640 | OV2640:OV2640 | $10.10 | $10.10 | $10.10 | [LCSC](https://www.lcsc.com/product-detail/C359962.html) |
| D1 | 1 | PESD5V0L1ULD | Diode_SMD:D_SOD-882D | $0.0980 | $0.0980 | $0.0980 | [LCSC](https://www.lcsc.com/product-detail/C85380.html) |
| D2 | 1 | LED | LED_SMD:LED_1210_3225Metric | $0.0300 | $0.0300 | $0.0300 | [LCSC](https://www.lcsc.com/category/110.html) |
| J1 | 1 | USB_C_Receptacle_USB2.0_16P | Connector_USB:USB_C_Receptacle_G-Switch_GT-USB-7010ASV | $0.1149 | $0.1149 | $0.1149 | [LCSC](https://www.lcsc.com/category/842.html) |
| J2 | 1 | Micro_SD_Card_Det1 | Connector_Card:microSD_HC_Molex_104031-0811 | $0.6304 | $0.6304 | $0.6304 | [LCSC](https://www.lcsc.com/product-detail/C585350.html) |
| Q1 | 1 | FDN340P | Package_TO_SOT_SMD:SOT-23 | $0.1763 | $0.1763 | $0.1763 | [LCSC](https://www.lcsc.com/product-detail/C75469.html) |
| R1,R2 | 2 | 5000 | Resistor_SMD:R_01005_0402Metric | $0.0200 | $0.0400 | $0.0400 | [Mouser](https://www.mouser.com/c/passive-components/resistors/film-resistors/thick-film-resistors-smd/?case+code+-+in=01005&resistance=10+kOhms) |
| R3 | 1 | 0 | Resistor_SMD:R_0805_2012Metric | $0.0100 | $0.0100 | $0.0100 | [LCSC](https://www.lcsc.com/category/439.html) |
| R4 | 1 | 2k | Resistor_SMD:R_01005_0402Metric | $0.0200 | $0.0200 | $0.0200 | [Mouser](https://www.mouser.com/c/passive-components/resistors/film-resistors/thick-film-resistors-smd/?case+code+-+in=01005&resistance=10+kOhms) |
| R5 | 1 | 470R | Resistor_SMD:R_01005_0402Metric | $0.0200 | $0.0200 | $0.0200 | [Mouser](https://www.mouser.com/c/passive-components/resistors/film-resistors/thick-film-resistors-smd/?case+code+-+in=01005&resistance=10+kOhms) |
| R6 | 1 | 25k | Resistor_SMD:R_01005_0402Metric | $0.0200 | $0.0200 | $0.0200 | [Mouser](https://www.mouser.com/c/passive-components/resistors/film-resistors/thick-film-resistors-smd/?case+code+-+in=01005&resistance=10+kOhms) |
| R7,R9,R10,R11,R12,R13,R14,R15 | 8 | 10k | Resistor_SMD:R_01005_0402Metric | $0.0200 | $0.1600 | $0.1600 | [Mouser](https://www.mouser.com/c/passive-components/resistors/film-resistors/thick-film-resistors-smd/?case+code+-+in=01005&resistance=10+kOhms) |
| R8 | 1 | 100R | Resistor_SMD:R_01005_0402Metric | $0.0200 | $0.0200 | $0.0200 | [Mouser](https://www.mouser.com/c/passive-components/resistors/film-resistors/thick-film-resistors-smd/?case+code+-+in=01005&resistance=10+kOhms) |
| R16,R17 | 2 | 4.7k | Resistor_SMD:R_01005_0402Metric | $0.0200 | $0.0400 | $0.0400 | [Mouser](https://www.mouser.com/c/passive-components/resistors/film-resistors/thick-film-resistors-smd/?case+code+-+in=01005&resistance=10+kOhms) |
| SW1 | 1 | SW_SPST | Button_Switch_SMD:SW_SPST_B3U-1000P-B | $0.1965 | $0.1965 | $0.1965 | [LCSC](https://www.lcsc.com/product-detail/C231329.html) |
| SW2,SW3,SW4 | 3 | SW_Push | Button_Switch_SMD:SW_Push_1P1T_NO_CK_KSC6xxJ | $0.7400 | $2.22 | $0.2112 | [Mouser](https://www.mouser.com/c/electromechanical/switches/tactile-switches/?m=C%26K+Switches&series=KSC6) |
| U1 | 1 | USBLC6-2SC6 | Package_TO_SOT_SMD:SOT-23-6 | $0.1523 | $0.1523 | $0.1523 | [LCSC](https://www.lcsc.com/product-detail/C7519.html) |
| U2 | 1 | MCP73831-2-OT | Package_TO_SOT_SMD:SOT-23-5 | $0.3922 | $0.3922 | $0.3922 | [LCSC](https://www.lcsc.com/product-detail/C424093.html) |
| U3 | 1 | MAX604 | Package_DIP:DIP-5-6_W7.62mm_Socket_LongPads | $8.11 | $8.11 | $0.0895 | [Mouser](https://www.mouser.com/c/semiconductors/power-management-ics/voltage-regulators-voltage-controllers/ldo-voltage-regulators/?series=MAX604) |
| U4 | 1 | ESP32-S3-WROOM-1 | RF_Module:ESP32-S3-WROOM-1 | $3.75 | $3.75 | $3.75 | [LCSC](https://www.lcsc.com/product-detail/C2913199.html) |
| U5 | 1 | EMMC08G-MB29-PM9B | EMMC08G-MB29-PM9B:BGA153N50P14X14_1300X1150X100N | $16.32 | $16.32 | $0.0000 | [Win Source](https://www.win-source.net/products/detail/kingston/emmc08g-mb29-pm9b.html) |




### Sourcing from Shenzhen

Almost all of the low cost parts can be sourced through LCSC.com or similar Chinese electronics suppliers. The target total is lower than the current total because some high cost or optional parts need cheaper substitutes or should be treated as optional, especially the eMMC and regulator.

For less traceable sources, I used a variety of resources to find these alternate parts and where to source them from. For one, this webiste https://www.travelchinaguide.com/cityguides/guangdong/shenzhen-electronics-malls.htm lists the 8 electronics malls in Shenzhen. Huaqiang obviously being the biggest, multiple youtube videos cite what things vendors sell in particular markets. This video from Lady Adafruit covers the book "The Essential Guide to Electronics in Shenzhen", and also describes some parts she was able to buy and where, as well as some useful tips to sourcing the right part.



| Build Option | Estimated Consumed BOM Cost |
|---|---:|
| All parts | $34.45 |
| All parts w/ eMMC optional | $18.13 |
| eMMC optional + AP2112K LDO substitute | $16.41 |


**Note that although total cost is cheap, vendors probably won't sell you individual parts b/c of MOQ. This probably means you'd have to multiply the cheaper parts by 100 (e.g. buying 100 resistors). With MOQ, we can expect up to $100 total.



| Ref | Qty | Value | Suggested Shenzhen Part | Supplier / Part # | Source | Unit Price | BOM Cost | Status |
|---|---:|---|---|---|---|---:|---:|---|
| BT1 | 1 | Battery_Cell | Keystone 103 | C238065 | [LCSC/JLC local China channel](https://www.lcsc.com/product-detail/BatteryConnector_Keystone-103_C238065.html) | $1.08 | $1.08 | Populate |
| C1,C2,C4 | 3 | 4u7 | Murata GRM033R60J475ME05D / JLC equiv. | C3863497 | [JLCPCB SMT assembly](https://jlcpcb.com/partdetail/4431990-GRM033R60J475ME05D/C3863497) | $0.04 | $0.12 | Populate |
| C3,C7,C11,C14,C16 | 5 | 4.7uF | Murata GRM033R60J475ME05D / JLC equiv. | C3863497 | [JLCPCB SMT assembly](https://jlcpcb.com/partdetail/4431990-GRM033R60J475ME05D/C3863497) | $0.04 | $0.20 | Populate |
| C5,C6 | 2 | 10uF | JLC 0201 high-cap MLCC / verify exact PN | C9900079312 / verify | [JLCPCB SMT assembly / consign if needed](https://jlcpcb.com/partdetail/JLCPCBAssembly-BTR02D3/C9900079312) | $0.04 | $0.08 | Populate |
| C8,C9,C10,C12,C13,C15,C18 | 7 | 100nF | FH 0201X104K100NT | C284966 | [LCSC](https://www.lcsc.com/product-detail/C284966.html) | $0.00 | $0.01 | Populate |
| CAM1 | 1 | OV2640 | Waveshare OV2640 Camera Board | C359962 | [LCSC](https://www.lcsc.com/product-detail/C359962.html) | $10.10 | $10.10 | Populate |
| D1 | 1 | PESD5V0L1ULD | LRC LESD8D5.0CAT5G | C172411 | [LCSC alternative](https://www.lcsc.com/product-detail/C172411.html) | $0.01 | $0.01 | Populate |
| D2 | 1 | LED | Vishay SB1210WC01-RG or cheaper local 1210 LED | C6472940 | [LCSC / local HQB bin alternative](https://www.lcsc.com/product-detail/C6472940.html) | $0.31 | $0.31 | Populate |
| J1 | 1 | USB_C_Receptacle_USB2.0_16P | G-Switch GT-USB-7010ASV | C2988369 | [LCSC](https://www.lcsc.com/product-detail/C2988369.html) | $0.08 | $0.08 | Populate |
| J2 | 1 | Micro_SD_Card_Det1 | XKB Connectivity XKTF-015-N | C381082 | [LCSC](https://www.lcsc.com/product-detail/C381082.html) | $0.06 | $0.06 | Populate |
| Q1 | 1 | FDN340P | TECH PUBLIC FDN340P | C2890122 | [LCSC](https://www.lcsc.com/product-detail/mosfets_tech-public-fdn340p_C2890122.html) | $0.06 | $0.06 | Populate |
| R1,R2 | 2 | 5000 | Generic 01005 1% resistor / value match | BOM/RFQ | [LCSC RFQ / local reels](https://www.lcsc.com/product-detail/C2889342.html) | $0.00 | $0.01 | Populate |
| R3 | 1 | 0 | YAGEO/UNI-ROYAL 0R 0805 | BOM/RFQ | [LCSC / local reels](https://www.lcsc.com/category/1199.html) | $0.00 | $0.00 | Populate |
| R4 | 1 | 2k | Generic 01005 1% resistor / value match | BOM/RFQ | [LCSC RFQ / local reels](https://www.lcsc.com/product-detail/C2889342.html) | $0.00 | $0.00 | Populate |
| R5 | 1 | 470R | Generic 01005 1% resistor / value match | BOM/RFQ | [LCSC RFQ / local reels](https://www.lcsc.com/product-detail/C2889342.html) | $0.00 | $0.00 | Populate |
| R6 | 1 | 25k | Generic 01005 1% resistor / value match | BOM/RFQ | [LCSC RFQ / local reels](https://www.lcsc.com/product-detail/C2889342.html) | $0.00 | $0.00 | Populate |
| R7,R9,R10,R11,R12,R13,R14,R15 | 8 | 10k | VO 0402 ±1% 10K / 01005 RFQ if keeping footprint | C2889342 / RFQ | [LCSC / RFQ](https://www.lcsc.com/product-detail/C2889342.html) | $0.00 | $0.01 | Populate |
| R8 | 1 | 100R | Generic 01005 1% resistor / value match | BOM/RFQ | [LCSC RFQ / local reels](https://www.lcsc.com/category/1199.html) | $0.00 | $0.00 | Populate |
| R16,R17 | 2 | 4.7k | Generic 01005 1% resistor / value match | BOM/RFQ | [LCSC RFQ / local reels](https://www.lcsc.com/category/1199.html) | $0.00 | $0.01 | Populate |
| SW1 | 1 | SW_SPST | OMRON B3U-1000P | C231329 | [LCSC/JLCPCB](https://www.lcsc.com/product-detail/C231329.html) | $0.20 | $0.20 | Populate |
| SW2,SW3,SW4 | 3 | SW_Push | CAX TS3425PA-3x4x2.5-160 | C51927438 | [LCSC](https://www.lcsc.com/product-detail/C51927438.html) | $0.04 | $0.13 | Populate |
| U1 | 1 | USBLC6-2SC6 | TECH PUBLIC USBLC6-2SC6 | C2827654 | [LCSC](https://www.lcsc.com/product-detail/C2827654.html) | $0.04 | $0.04 | Populate |
| U2 | 1 | MCP73831-2-OT | Microchip MCP73831T-2ACI/OT | C424093 | [LCSC](https://www.lcsc.com/product-detail/C424093.html) | $0.39 | $0.39 | Populate |
| U3 | 1 | MAX604 | MAX604ESA+T / MAX604CSA+T from Alibaba, or AP2112K-3.3TRG1 substitute | Alibaba / C51118 | [Alibaba Shenzhen seller / LCSC substitute](https://m.alibaba.com/showroom/max604esa--t.html) | $1.88 | $1.88 | Populate |
| U4 | 1 | ESP32-S3-WROOM-1 | ESP32-S3-WROOM-1-N8R8 | C2913201 | [LCSC](https://www.lcsc.com/product-detail/C2913201.html) | $3.36 | $3.36 | Populate |
| U5 | 1 | EMMC08G-MB29-PM9B | Kingston EMMC08G-MB29-PM9B exact; Kioxia THGBMNG5D1LBAIL alt | Win-Source / C391255 | [Win-Source / LCSC alternative](https://www.win-source.net/products/detail/kingston/emmc08g-mb29-pm9b.html) | $16.32 | $16.32 | DNP / optional footprint |







---


## 2. Block Diagram

<img width="1261" height="888" alt="image" src="https://github.com/user-attachments/assets/8dd7ad94-7d2d-44f0-be11-53f7d763d030" />


This block diagram represents the major systems of this PCB. The power comes in as 5v into USB-C, which goes into a LiPo battery charging module. At that point, voltage drops to around a nominal value of 3.7V because of the MCP. This circuit is one way and therefore USB-C only charges the battery, not powering the ESP. The LiPo battery is rated to output around 3.7V, and is then passed through a 3.3V voltage regulator. I used the MAX604 LPO, which I'll explain later. The ESP32-S3-WROOM1 is the main controller which will operate fine from ~2.9-3.3V at 500mA. 

This PCB has two means of storage: A MicroSD, or eMMC. To keep the SD card separate from the BOM, I just used a MicroSD card detector. To keep the eMMC separate from the BOM, I used a custom eMMC footprint that I found off SnapMagic.

For the camera module, I went with the OV2640 because it was the easiest camera to work with. It operatres fine under ~1.7V-3.3V which is what we expect to be at. The camera also supports 800×600 at 30 FPS, which is already much better than the requirements. 

Finally, we have three push switches for start/stop recording, boot, and reset.


---


## 3. Schematic Design

Here are some youtube videos that I used to help along:

-https://www.youtube.com/watch?v=-iZbwzr0dS8
-https://www.youtube.com/shorts/hBdJ9uH2Yd4
-https://www.youtube.com/watch?v=GRd9uTwg7r4
-https://www.youtube.com/watch?v=S24RvYZWYUQ
-https://www.youtube.com/watch?v=g40tUdjZ-Sk
-https://www.youtube.com/watch?v=POPvclRAKOQ
-https://www.youtube.com/watch?v=Ah65M31v87c


### Full View of Schematic

<img width="907" height="607" alt="image" src="https://github.com/user-attachments/assets/62841585-c328-469a-b9e5-9706b14695b0" />  


## ERC Passing

<img width="710" height="455" alt="image" src="https://github.com/user-attachments/assets/4f619369-4c5e-4be2-ad6b-5cdb8933712b" />    



## 4. Schematic Breakdown


### USB-C Power Entry


<img width="500" height="388" alt="image" src="https://github.com/user-attachments/assets/ae17c6a2-d1ae-4d19-ac5c-3ce5ce03ea7c" />


I use 5k resistors as pull down for CC1 and CC2 per the datasheet. I use a USBC connector to protect the data lines and route it to D- and D+. The diode I use has a clamping voltage of 12v, so under normal 5v operations it doesn't activate, but in cases of voltage spikes, it'll short to ground. I use 4.7uF capacitors for decoupling per the datasheet. This is a recurring value throughout the pcb. 



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





## 5. PCB Views

Note: The biggest thing here is that I did not finish applying the routes. Because of this, it does not pass the DRC test yet.

I used 4 layers for this PCB to sort of dedicate each layer to a solid reference plane, which should reduce noise and increase stability. I used this video to help: https://www.youtube.com/watch?v=Z7ycNfVJSJ4


<img width="534" height="543" alt="image" src="https://github.com/user-attachments/assets/2ddb1cf7-ba6c-43f7-b03d-4893e59abe64" />


<img width="780" height="562" alt="image" src="https://github.com/user-attachments/assets/30d4ab94-f8da-4984-801e-8e991735d262" />





## 6. Manufacturing in Shenzhen

The PCB would be about 149.5mm x 137.0mm or about 5.9in x 5.4in. This is pretty large but this is quite a crude and very unpolished version in terms of
optimizing space, traces, layers, etc. Getting this manufactured in Shenzhen is should be easy. One company, NextPCB, is connected with Shenzhen Huaqiu Intelligent Connectivity, and lists its headquarters in Shenzhen. Seeed Studio Fusion is another Shenzhen based prototyping service that offers PCB manufacturing and PCB assembly as well as making custom parts.



## 7. 3D Printed Casing

Ideally this mini project would be interfaced with a 3D printed casing to finish off the "spy camera" look. But, I did not create the model yet.
