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

<p style={{textAlign: 'center'}}><img src="https://raw.githubusercontent.com/Longan-Labs/XIAO_MATRIX_RES/main/images/1-6x10-RGB-MATRIX-for-XIAO-45font.jpg" alt="pir" width={600} height="auto" /></p>

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
*Refer to the image provided in the documentation for a visual guide.*

// 一张焊接好的图片

### 2. Connecting the Expansion Board:
Once the soldering is complete, you can proceed to connect the expansion board to the XIAO RP2040 main controller.
*Again, refer to the accompanying image in the documentation for clarity.*

### 3. Connecting to Your Computer:
For programming the XIAO RP2040, you'll need a TYPE-C USB data cable. Connect one end to the XIAO RP2040 and the other to your computer. For a detailed guide on programming the XIAO RP2040, please refer to this [documentation](https://wiki.seeedstudio.com/XIAO-RP2040/).

// 一张插到电脑的图片

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

<div className="altium-ecad-viewer" data-project-src="https://github.com/Longan-Labs/XIAO_MATRIX_RES/raw/main/EAGLE_XIAO_MATRIX.zip" style={{borderRadius: '0px 0px 4px 4px', height: 500, borderStyle: 'solid', borderWidth: 1, borderColor: 'rgb(241, 241, 241)', overflow: 'hidden', maxWidth: 1280, maxHeight: 700, boxSizing: 'border-box'}}>
</div>

## FAQ

- Q1: Do I need to solder anything when I receive the product?
- A1: If you intend to use the board in conjunction with the XIAO main controller, you'll need to solder the provided pin headers. However, if you're using the board in a different setup, soldering might not be necessary.

- Q2: How do I power the 6x10 RGB-MATRIX?
- A3: The matrix can be powered through the XIAO's 5V supply or directly via the VCC solder pad with a 5V source.

- Q3: The LEDs aren't lighting up. What should I do?
- A4: Ensure that your soldering is done correctly, the matrix is properly connected to the XIAO main controller, and the correct code has been uploaded. If issues persist, refer to the official documentation or contact Seeed Studio support.

- Q4: Can I integrate this matrix into wearable tech or clothing?
- A5: Given its compact design, the 6x10 RGB-MATRIX can be integrated into various projects, including wearable tech. However, ensure that the connections are secure and the matrix is protected from excessive wear and tear.

- Q5: Can I chain multiple expansion boards together?
- A6: Yes, you can. However, some soldering will be required. You'll need to solder the DOUT of the preceding board to the DIN of the next board, and also connect the VCC and GND solder pads together.

## Resources

- **[Zip]** [Eagle file](https://github.com/Longan-Labs/XIAO_MATRIX_RES/raw/main/EAGLE_XIAO_MATRIX.zip)
- **[PDF]** [Datasheet - WS2812B](https://github.com/Longan-Labs/XIAO_MATRIX_RES/blob/main/WS2812B-1010-DATASHEET.PDF)
- **[GITHUB]** [Library for WS2812B](https://github.com/adafruit/Adafruit_NeoPixel)

## Tech Support
If you have any technical issue.  submit the issue into our [forum](https://forum.seeedstudio.com/).