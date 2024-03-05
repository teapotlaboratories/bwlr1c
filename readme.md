

  
# Teapotlabs BWLR1C
 <p align="center"> <img src="https://raw.githubusercontent.com/teapotlaboratories/bwlr1c/main/docs/images/device.jpg" alt="drawing"  width="50%" height="50%"/></p>
 
Teapotlabs BWLR1C is a wireless LoRa environmental sensor capable of sensing temperature, humidity, air pressure and air quality using the on-board BME680.
This device is an updated to **Teapotlabs BWLR1B,** by using the an on-board antenna.
By using an STM32WLE MCU, the device is capable of multi-year operation before changing the batteries

Teapotlabs BWLR1C is part of  [Teapot open-hardware project](https://github.com/teapotlaboratories).

## Disclaimer
- The 1KM range is based on [AERQ - Air Quality Monitoring](https://www.seeedstudio.com/blog/2022/04/27/monitoring-indoor-air-pollutants-the-silent-issue-for-smart-city-iot-using-seeed-lora-e5-and-fusion-pcba/) design, but have not been tested on this device yet
- The position of the BME680 sensor on the board might not be the most efficient

## Future Works
- Change `SW4` wiring from GND to 3V3, to allow booting to STM32WLE USART Bootloader. This enable the user to flash the RAK3172 module using STM32CubeProgrammer without ST-Link.

## Specification

- [RAK3172](https://docs.rakwireless.com/Product-Categories/WisDuo/RAK3172-Module/Overview/): An STM32WLE5CC module
- 3.3V only power/pin. 
- 2uA Deep-Sleep
- BME680 for Environmental Sensing
- Switchable TX Power. 14 dBm(50mA) or 22 dBm(140mA) ( on 915MHz frequency )
- Supports LoRaWAN 1.0.3
- 1KM Range
- UART2 breakout for **Arduino** progamming
- SWD breakout for **Mbed OS/STM32Cube** programming
- SMA antenna connector
- **CR2450** battery holder *xor* **AA** battery holder
- Capacitor ( [optional to prolong CR2450 usage](https://www.rs-online.com/designspark/can-i-prolong-my-coin-cell-battery-life-with-a-capacitor) )

> Based-on [TI's White Paper](https://www.ti.com/lit/wp/swra349/swra349.pdf), using coin-cell to draw short high-power pulses (~40mA) is possible, but will reduce the effective capacity of the battery. The White Paper proposed a solution to increase the effective capacity
## Schematics

<p align="center"> <img src="https://raw.githubusercontent.com/teapotlaboratories/bwlr1c/main/hardware/schematic.png" alt="schematic"/></p>

## Boards
 <p align="center">  <img src="https://github.com/teapotlaboratories/bwlr1c/raw/main/docs/images/pcb_render.gif" alt="pcb_render"  width="50%" height="50%"/><br><b>PCB Render</b></p>

Built using KiCAD, the board is design to be as small as possible when operated using CR2450 coin-cell batteries

| Top Board | Bottom Board |
|--|--|
| <p align="center"> <img src="https://github.com/teapotlaboratories/bwlr1c/raw/main/docs/images/assembled_top.jpg" alt="assembled_front"  width="77%" height="77%"/></p> | <p align="center"> <img src="https://github.com/teapotlaboratories/bwlr1c/raw/main/docs/images/assembled_bottom.jpg" alt="assembled_back"  width="100%" height="100%"/></p> |
| <p align="center"> <img src="https://github.com/teapotlaboratories/bwlr1c/raw/main/docs/images/pcb_top.png" alt="pcb_front"  width="90%" height="90%"/></p> | <p align="center"> <img src="https://github.com/teapotlaboratories/bwlr1c/raw/main/docs/images/pcb_bottom.png" alt="pcb_bottom"  width="50%" height="50%"/></p> |

 <p align="center"> <img src="https://github.com/teapotlaboratories/bwlr1c/raw/main/hardware/pcb.png" alt="pcb"  width="50%" height="50%"/><br><b>PCB Top and Bottom Layout</b></p> 
  
### Case
<p align="center">  <img src="https://github.com/teapotlaboratories/bwlr1c/raw/main/docs/images/case_render.gif" alt="case_render"  width="80%" height="80%"/></p>

Built using [TinkerCAD](https://www.tinkercad.com), the cases are available for the CR2450 variant and the AA variant, 3D printable with any generic 3D printer with/without suppport (depends on the orientation). The STL files are available [here](https://github.com/teapotlaboratories/bwlr1c/tree/main/hardware/case)
 <p align="center"><img src="https://github.com/teapotlaboratories/bwlr1c/raw/main/docs/images/case_open.jpg" alt="drawing"  width="50%" height="50%"/><br><b>Case Open</b></p>

The case is design to be as small as possible with an additional magnets in the back to ease the placement of the sensor. The following are the list of material used at the time of testing:
- 4 piece of 8mm x 2mm neodymium magnet

<p align="center"><img src="https://github.com/teapotlaboratories/bwlr1c/raw/main/docs/images/placement_showcase.gif" alt="placement_showcase"  width="50%" height="50%"/><br><b>Sensor Placement with Magnet</b></p>

### Measurement
Power consumption and solar charging current are measured using [Nordic PPK2](https://www.nordicsemi.com/Products/Development-hardware/Power-Profiler-Kit-2).
The following are the summary of the measurement:
- Transmit 14dBm:  443ms @ 47mA
- Deep-Sleep : 2 uA

<p align="center"><img src="https://github.com/teapotlaboratories/bwlr1c/raw/main/docs/measurement/deep_sleep.png" alt="deep_sleep"  width="90%" height="90%"/><br><b>Deep-Sleep</b></p>

<p align="center"><img src="https://github.com/teapotlaboratories/bwlr1c/raw/main/docs/measurement/bme680_measure_and_lora_transmit.png" alt="bme688_measure_and_lora_transmit"  width="90%" height="90%"/><br><b>BME688 Measure and LoRa Transmit</b></p>

More measurement can be found [here](https://github.com/teapotlaboratories/bwlr1c/tree/main/docs/measurement)


### Bill Of Materials
Most of the components are generic and can be bought from any electornics/semi-conductor distributor. RAK3172 is the only component available in [RAKwireless store](https://store.rakwireless.com/products/wisduo-lpwan-module-rak3172?variant=40014759493830). The bill of materials can be downloaded [here](https://github.com/teapotlaboratories/bwlr1c/raw/main/hardware/bill_of_materials.csv)

> :warning: **Be sure to buy the RAK3172 variant without IPEX to use the On-Board Antenna** 

|Id |Designator                      |Package                           |Quantity|Designation   |Notes                            |
|---|--------------------------------|----------------------------------|--------|--------------|---------------------------------|
|1  |C5,C12,C11,C3                   |C_1206_3216Metric                 |4       |100nF         |                                 |
|2  |SW4                             |SW_SPST_Omron_B3FS-100xP          |1       |BOOT          |                                 |
|3  |R7,R2,R3,R6                     |R_1206_3216Metric                 |4       |10K           |                                 |
|4  |C9,C8,C10,C2,C4,C13,C14,C6,C1,C7|CP_EIA-3528-15_AVX-H              |10      |330uF         |Optional                         |
|5  |R5                              |R_1206_3216Metric                 |1       |1K            |                                 |
|6  |E1                              |XDCR_ANT-915-USP410               |1       |ANT-915-USP410|                                 |
|7  |SW3                             |SW_SPST_Omron_B3FS-100xP          |1       |RESET         |                                 |
|8  |U1                              |BME680-PSON80P300X300X100-8N      |1       |BME680        |                                 |
|9  |U2                              |RAK3172                           |1       |RAK3172       |                                 |
|10 |Q1                              |SOT-23                            |1       |AO3407        |                                 |
|11 |BT3,BT1                         |BatteryHolder_Keystone_3008_1x2450|2       |CR2450        |Mutual Exclusive with BT2        |
|12 |BT2                             |BatteryHolder_Keystone_2462_2xAA  |1       |2x AA         |Mutual Exclusive with BT3 and BT1|


## Programming
Programming the device can be done over the **UART2** or **SWD**, available next to the On-board antenna.
Out of the factory, the RAK3172 chip ships with an **AT firmware** that can be tested by connecting a USB-to-UART bridge to the **UART2** port.

The following are some very good tutorial to start developing with the device:

- [Communicating with the AT firmware](https://docs.rakwireless.com/Product-Categories/WisDuo/RAK3172-Module/Quickstart/#rak3172-as-a-lora-lorawan-modem-via-at-command)
 - [Programming with Arduino](https://docs.rakwireless.com/Product-Categories/WisDuo/RAK3172-Module/Quickstart/#rak3172-as-a-stand-alone-device-using-rui3)
 - [Programming with STM32Cube](https://docs.rakwireless.com/Product-Categories/WisDuo/RAK3172-Module/Low-Level-Development/#rak3172-on-stm32cubeide-with-stm32wl-sdk-v1-0-0)
 - [Programming with MbedOS](https://github.com/hallard/LoRa-E5-Tiny/blob/main/README.md#compile-and-flash-firmware)

For connecting to the **UART2** port, use any USB-to-UART bridge module. In testing, the [Sparkfun](https://www.sparkfun.com/products/14050) board is used for communication with AT firmware and programming over **Arduino**.
 <p align="center"> <img src="https://raw.githubusercontent.com/teapotlaboratories/bwlr1c/main/docs/images/sparkfun_ftdi.jpeg" width="30%" height="30%"><br>Sparkfun USB-to-UART Bridge</p>

> :warning: **Be sure to only use 3.3V module. Do not 5V module** 

For connecting to the **SWD** port, use ST-Link v2  in-circuit debugger and programmer from STM. In testing, ST-Link v2 clone will not work. The ST-Link v2 should atleast be reconizeable by the [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html).
A cheap and alternative way to get an authorized ST-Link is to buy a Nucleo board, cut the top part which contain the ST-Link and use it as an external programmer.
 <p align="center"> <img src="https://raw.githubusercontent.com/teapotlaboratories/bwlr1c/main/docs/images/nucleo_st-linkv2.jpeg" width="70%" height="70%"><br>ST-Link v2 from a Nucleo Development Board</p>
Here are some good tutorial to convert a Nucleo to and external ST-Link v2:

 - https://www.radioshuttle.de/en/turtle-en/nucleo-st-link-interface-en/
 - https://jeelabs.org/book/1547a/index.html

## Notes
There are some issue, notes, and behavior that was discovered at the time of testing and development. The following are those discovery:
- Using Arduino RUI3 framework may introduce some-instability after programming. It is observed that by randomly power-cycling the board in-short interval after flashing, causes the board to hang in Boot mode. The fix is currently on the works.

## Reference
The project won't be possible without the amazing work from people across the globe. The following are the reference to those awesome projects:

 - [LoRa e5 Tiny](https://github.com/hallard/LoRa-E5-Tiny)
 - [AERQ - Air Quality Monitoring](https://www.seeedstudio.com/blog/2022/04/27/monitoring-indoor-air-pollutants-the-silent-issue-for-smart-city-iot-using-seeed-lora-e5-and-fusion-pcba/)

## License
The product is open-source! However, some part of library used under **src**, might have it's own license.
Please reach out or create a ticket to report any license violation.

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
