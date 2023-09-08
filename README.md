---
description: TBD
title: TBD
keywords:
- XIAO
image: TBD
slug: XIAO IO
last_update:
  date: 8-10-2023
  author: Stephen Lo
---

<p style={{textAlign: 'center'}}><img src="https://raw.githubusercontent.com/Longan-Labs/XIAO_IO_EXPANDER_BOARD/main/images/2-103030415-GPIO-Expander-for-XIAO-font.jpg" alt="pir" width={600} height="auto" /></p>

The GPIO Expander for XIAO is a state-of-the-art expansion board designed to enhance the capabilities of the Seeed Studio XIAO series. Powered by the MCP23017 chip, this board offers an additional 16 GPIO pins, allowing users to expand their projects without constraints. Whether you're a hobbyist looking to experiment with more components or a professional seeking a reliable GPIO expansion solution, this board is tailored to meet your needs. Its compatibility with the XIAO series ensures seamless integration, making your development process smoother and more efficient.
<p style={{textAlign: 'center'}}><a href="https://www.seeedstudio.com/-Grove-VOC-and-eCO2-Gas-Sensor-(SGP30)-p-3071.html" target="_blank"><img src="https://files.seeedstudio.com/wiki/Seeed-WiKi/docs/images/300px-Get_One_Now_Banner-ragular.png" /></a></p>

## Features

- Seamless Integration with XIAO: Designed to work perfectly with the Seeed Studio XIAO series.
- 16 Additional GPIO Pins: Powered by the MCP23017, it provides 16 extra GPIO pins for your projects.
- I2C Interface with Configurable Address: Default I2C address is 0x21, but can be configured to 0x20.
- Robust Design: Built with high-quality materials to ensure longevity and reliability.

## Specification

- Chip: MCP23017
- Number of GPIO Pins: 16
- Communication Protocol: I2C
- Default I2C Address: 0x21 (Configurable to 0x20)
- Operating Voltage: 3.3V
- Dimensions: 21mm x 17mm

## Applications

The GPIO Expander for XIAO is versatile and can be used in a multitude of applications, including but not limited to:

- Home Automation Systems: Expand the number of devices you can control in your smart home setup.
- Robotics: Add more sensors, motors, or other components to your robot without running out of GPIO pins.
- Gaming Consoles: Design custom controllers or other peripherals with a plethora of buttons and switches.
- Industrial Control Systems: Manage more devices and sensors in your industrial setup.
- Educational Projects: Teach students about microcontrollers and electronics without being limited by the number of GPIO pins.

## Getting Started

Welcome to the quick start guide for the IO Expander for XIAO. This guide aims to help you set up and get started with your new IO Expander board in conjunction with the XIAO RP2040 main controller.

### 1. Soldering the Headers:
Upon receiving your product, some soldering will be required. We've provided two pin headers with the package. You'll need to solder these headers onto the expansion board. 

### 2. Connecting the Expansion Board:
Once the soldering is complete, you can proceed to connect the expansion board to the XIAO RP2040 main controller.

### 3. Connecting to Your Computer:
For programming the XIAO RP2040, you'll need a TYPE-C USB data cable. Connect one end to the XIAO RP2040 and the other to your computer. For a detailed guide on programming the XIAO RP2040, please refer to this [documentation](https://wiki.seeedstudio.com/XIAO-RP2040/).

![](https://raw.githubusercontent.com/Longan-Labs/XIAO_IO_EXPANDER_BOARD/main/images/6-103030415-GPIO-Expander-for-XIAO-feature.jpg)

### 4. Installing the MCP23017 Library:
Before you can start programming the LEDs, you'll need a specific library for the RP2040. Download the MCP23017 library from this [GitHub link](https://github.com/Longan-Labs/Adafruit-MCP23017-Arduino-Library). Once downloaded, install the library in your programming environment.

### 5. Programming the board with Arduino IDE:
In the Arduino IDE, open a new sketch and copy the following example code:

```arduino
#include <Adafruit_MCP23X17.h>
Adafruit_MCP23X17 mcp;

void setup() {
    Serial.begin(9600);
    Serial.println("MCP23xxx Blink Test!");
    if (!mcp.begin_I2C()) {
        Serial.println("Error.");
        while (1);
    }

    Serial.println("Looping...");

    for(int i=0; i<16; i++) {
        mcp.pinMode(i, OUTPUT);
    }
}

void loop() {
    for(int i=0; i<16; i++) mcp.digitalWrite(i, HIGH);
    delay(1000);
    for(int i=0; i<16; i++) mcp.digitalWrite(i, LOW);
    delay(1000);
}
```

Upload the above code to your XIAO RP2040. Once uploaded, with a multimeter, measure each IO pin. You will see the voltage jump between 3.3V and 0V, consistent with the blinking frequency in the code.

## Schematic Online Viewer

<div className="altium-ecad-viewer" data-project-src="https://github.com/Longan-Labs/XIAO_IO_EXPANDER_BOARD/raw/main/XIAO_IO.zip" style={{borderRadius: '0px 0px 4px 4px', height: 500, borderStyle: 'solid', borderWidth: 1, borderColor: 'rgb(241, 241, 241)', overflow: 'hidden', maxWidth: 1280, maxHeight: 700, boxSizing: 'border-box'}}>
</div>

## FAQ

### 1. Why isn't my GPIO Expander for XIAO responding?

**Answer**: Ensure that the XIAO module is correctly plugged into the expansion board. Also, check if the necessary libraries are installed and the correct board and port are selected in the Arduino IDE.

### 2. Can I use the GPIO Expander for XIAO with other microcontrollers?

**Answer**: Yes, the GPIO Expander is designed primarily for the XIAO module, but it can be used with other microcontrollers that support I2C communication. You might need to adjust the code and connections accordingly.

### 3. How do I change the I2C address of the MCP23017 chip on the GPIO Expander for XIAO?

**Answer**: The default I2C address is set to 0x21. If you want to change it to 0x20, there's a jumper labeled "J2" on the board. You'll need to solder the J2 jumper to change the address.

### 4. I'm getting noise or erratic behavior on my GPIO pins. What could be the cause?

**Answer**: Ensure that the connections are secure and there's no interference. Using pull-up or pull-down resistors can help stabilize the input pins. Also, ensure that the power supply is stable and can provide the necessary current for all connected devices.


## Resources

- **[Zip]** [Eagle file](https://github.com/Longan-Labs/XIAO_IO_EXPANDER_BOARD/raw/main/XIAO_IO.zip)
- **[PDF]** [Datasheet - MCP23017](https://github.com/Longan-Labs/XIAO_IO_EXPANDER_BOARD/blob/main/MCP23017_Data_Sheet_DS20001952-2998473.pdf)

## Tech Support
If you have any technical issue.  submit the issue into our [forum](https://forum.seeedstudio.com/).