# HiLetgo 3.5 TFT LCD Guide

This repository provides a comprehensive guide on how to set up and use the HiLetgo 3.5" TFT LCD 480 x 320 pixels. I created this repository because this specific display is quite rare in the market and was a real headache to set up. Hopefully, this guide will save you time and frustration.

# Introduction

The HiLetgo 3.5" TFT LCD is a versatile display module compatible with various microcontrollers, including Arduino. This tutorial is based on my experience with the Arduino Mega 2560.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Requirements](#requirements)
- [Wiring Diagram](#wiring-diagram)
- [Setup Instructions](#setup-instructions)
- [Example Code](#example-code)
- [Troubleshooting](#troubleshooting)
- [References](#references)
- [License](#license)

## Introduction

The HiLetgo 3.5" TFT LCD is a versatile display module compatible with various microcontrollers, including Arduino. This tutorial is based on my experience with the Arduino Mega 2560.

## Features

- **Resolution:** 480 x 320 pixels
- **Interface:** SPI
- **Display Size:** 3.5 inches
- **Driver IC:** [RussianDrivers](https://github.com/amperka/UTFT/tree/master?tab=readme-ov-fil)
- **Operating Voltage:** 3.3V/5V
- **Touch Screen:** NO

## Requirements

### Hardware

- HiLetgo 3.5" TFT LCD
- Arduino Mega 2560
- Connecting wires (male - female)
- Breadboard (optional)

### Software

- Arduino IDE
- Libraries: Adafruit GFX, Adafruit TFTLCD (or any compatible library)

## Wiring Diagram

Here is a basic wiring diagram for connecting the HiLetgo 3.5" TFT LCD to an Arduino Mega 2560:

| TFT LCD Pin | Arduino Pin    |
|-------------|----------------|
| VCC         | 5V             |
| GND         | GND            |
| CS          | 10             |
| RESET       | 9              |
| DC/RS       | 8              |
| SDI(MOSI)   | 51             |
| SCK         | 52             |
| LED         | 3.3V           |
| SDO(MISO)   | 50 (optional)  |

For other microcontrollers, please refer to their respective pin mapping.

## Setup Instructions

1. **Connect the Hardware:**
   - Follow the wiring diagram above to connect your HiLetgo 3.5" TFT LCD to the Arduino Mega 2560.

2. **Install Libraries:**
   - Open the Arduino IDE.
   - Go to `Sketch` > `Include Library` > `Manage Libraries`.
   - Search for `Adafruit GFX` and `Adafruit TFTLCD` libraries and install them.

3. **Upload Example Code:**
   - Open the `graphicstest` example from `File` > `Examples` > `Adafruit TFTLCD`.
   - Adjust the pin definitions in the code to match your wiring.
   - Upload the code to your Arduino Mega 2560.

## Example Code

Here is a simple example c
