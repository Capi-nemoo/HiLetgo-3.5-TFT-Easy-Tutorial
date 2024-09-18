# HiLetgo 3.5" TFT LCD Guide

This guide provides detailed instructions on how to set up and use the HiLetgo 3.5" TFT LCD with a resolution of 480 x 320 pixels. I created this guide because this specific display can be quite a headache to set up. Hopefully, this guide will save you time and frustration.

## Table of Contents

1. [Introduction](#introduction)
2. [Features](#features)
3. [Requirements](#requirements)
4. [Wiring Diagram](#wiring-diagram)
5. [Setup Instructions](#setup-instructions)
6. [Example Code](#example-code)
7. [Troubleshooting](#troubleshooting)
8. [References](#references)
9. [License](#license)

------

## Introduction

The HiLetgo 3.5" TFT LCD is a versatile display module compatible with various microcontrollers, including the Arduino Mega 2560. This guide is based on my experience using the Arduino Mega 2560, and its purpose is to help you set up and use the display effectively.

## Features

- **Resolution**: 480 x 320 pixels
- **Interface**: 16-bit parallel
- **Display Size**: 3.5 inches
- **Driver IC**: HX8357B, HX8357C, ILI9481, or ILI9486
- **Operating Voltage**: 3.3V/5V
- **Touch Screen**: No

## Requirements

### Hardware

- HiLetgo 3.5" TFT LCD
- Arduino Mega 2560
- Connecting wires (male-to-male)
- Breadboard (optional)

### Software

- Arduino IDE
- **TFT_HX8357** library

## Wiring Diagram

Since this display uses a 16-bit parallel interface, it requires multiple connections to the Arduino Mega 2560. Below is the pin mapping:

### Control Pins

| TFT LCD Pin | Arduino Mega Pin                |
| ----------- | ------------------------------- |
| VCC         | 5V                              |
| GND         | GND                             |
| CS          | 40                              |
| RESET       | 38                              |
| RS (DC)     | 39                              |
| WR          | 41                              |
| RD          | 43                              |
| LED         | 3.3V (use a resistor if needed) |

### Data Pins

| TFT LCD Pin | Arduino Mega Pin |
| ----------- | ---------------- |
| DB0         | 22               |
| DB1         | 23               |
| DB2         | 24               |
| DB3         | 25               |
| DB4         | 26               |
| DB5         | 27               |
| DB6         | 28               |
| DB7         | 29               |
| DB8         | 30               |
| DB9         | 31               |
| DB10        | 32               |
| DB11        | 33               |
| DB12        | 34               |
| DB13        | 35               |
| DB14        | 36               |
| DB15        | 37               |

**Note**: Double-check the pin numbers and ensure all connections are secure.

## Setup Instructions

### 1. Connect the Hardware

- Follow the wiring diagram above to connect your HiLetgo 3.5" TFT LCD to the Arduino Mega 2560.
- Ensure all data and control pins are connected correctly.

### 2. Install the **TFT_HX8357** Library

- Download the **TFT_HX8357** library from the [GitHub repository](https://github.com/Bodmer/TFT_HX8357).
- Extract the contents of the ZIP file.
- Copy the **TFT_HX8357** folder to your Arduino libraries directory (usually `Documents/Arduino/libraries`).
- Restart the Arduino IDE for it to recognize the new library.

### 3. Configure the Library

- Navigate to the `User_Setup.h` file within the **TFT_HX8357** library folder.

- Open `User_Setup.h` with a text editor.

- Select the correct driver for your display:

  Uncomment the driver corresponding to your display and comment out the others. For example, if your display uses the **HX8357B** driver:

  ```
  cpp
  
  
  Copy code
  #define HX8357B
  //#define HX8357C
  //#define ILI9481
  //#define ILI9486
  ```

- Set the display dimensions:

  ```
  cpp
  
  
  Copy code
  #define HX8357_TFTWIDTH  320
  #define HX8357_TFTHEIGHT 480
  ```

- Configure the fonts you want to use. You can comment out unused fonts to save memory:

  ```
  cpp
  
  
  Copy code
  #define LOAD_GLCD   // Font 1
  #define LOAD_FONT2  // Font 2
  #define LOAD_FONT4  // Font 4
  #define LOAD_FONT6  // Font 6
  #define LOAD_FONT7  // Font 7
  #define LOAD_FONT8  // Font 8
  #define LOAD_GFXFF  // FreeFonts from Adafruit
  ```

- Save the changes to `User_Setup.h`.

### 4. Upload Example Code

- Open the Arduino IDE.
- Navigate to `File` > `Examples` > `TFT_HX8357` and select an example such as `graphicstest`.
- Verify that the code compiles without errors.
- Upload the code to your Arduino Mega 2560.

## Example Code

Here’s a simple example that displays text and shapes on the screen:

```
cpp


Copy code
#include <TFT_HX8357.h>  // Hardware-specific library

TFT_HX8357 tft = TFT_HX8357();  // Create screen object

void setup() {
  tft.init();
  tft.setRotation(1);  // Adjust screen rotation as needed
  tft.fillScreen(TFT_BLACK);

  // Display text
  tft.setTextColor(TFT_WHITE, TFT_BLACK);
  tft.setTextSize(2);
  tft.setCursor(50, 50);
  tft.println("Hello, World!");

  // Draw a circle
  tft.drawCircle(160, 120, 50, TFT_RED);
}

void loop() {
  // Your code here
}
```

**Explanation**:

- **tft.init()**: Initializes the display.
- **tft.setRotation(1)**: Sets the screen orientation.
- **tft.fillScreen(TFT_BLACK)**: Fills the screen with black.
- **tft.setTextColor(TFT_WHITE, TFT_BLACK)**: Sets the text and background colors.
- **tft.setTextSize(2)**: Sets the text size.
- **tft.setCursor(50, 50)**: Sets the cursor position.
- **tft.println("Hello, World!")**: Displays the text on the screen.
- **tft.drawCircle(160, 120, 50, TFT_RED)**: Draws a red circle.

## Troubleshooting

- **Blank Screen**: Verify all connections and ensure the correct driver is selected in `User_Setup.h`.
- **Compilation Errors**: Ensure the **TFT_HX8357** library is installed correctly and there are no conflicts with other libraries.
- **Incorrect Orientation**: Adjust the parameter in `tft.setRotation()`.

## References

- [TFT_HX8357 Library GitHub Repository](https://github.com/Bodmer/TFT_HX8357)
- [HiLetgo 3.5" TFT LCD Product Page](https://www.hiletgo.com/)