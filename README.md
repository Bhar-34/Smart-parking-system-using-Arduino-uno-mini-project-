# Smart Parking System (Arduino Uno)  
A simple smart parking prototype using Arduino Uno to detect free parking spaces and display availability.

## Table of contents
- [Overview](#overview)
- [Features](#features)
- [Hardware Required](#hardware-required)
- [Wiring / Circuit](#wiring--circuit)
- [Software](#software)
- [Installation & Upload](#installation--upload)
- [Usage / Testing](#usage--testing)
- [Troubleshooting](#troubleshooting)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Overview
This mini project implements a basic smart parking system using an Arduino Uno. Ultrasonic sensors (or IR sensors) are used to detect whether parking spots are occupied. The system aggregates sensor inputs and shows the number of available spots on an LCD or 7-segment display, and can optionally trigger LEDs or a buzzer for guidance.

Use this project as a prototype or learning exercise to understand microcontroller input/output, sensor integration, and simple decision logic for real-world physical systems.

## Features
- Detects occupancy for N parking spots (expandable)
- Displays the number of free spots
- Visual indicators (LEDs) for available/occupied status
- Optionally supports serial output for debugging or connecting to a gateway

## Hardware required
- 1 × Arduino Uno (or compatible)
- 1 × 16x2 I2C LCD (or 16x2 parallel LCD + appropriate wiring)
- 1+ × Ultrasonic sensor(s) (HC-SR04) OR Infrared proximity sensors (one per spot)
- 1 × Buzzer (optional)
- LEDs and resistors for indicators (optional)
- Breadboard and jumper wires
- USB cable for programming the Arduino
- (Optional) Power supply if not using USB

## Wiring / Circuit
Example using one HC-SR04 per spot:
- HC-SR04 VCC → 5V
- HC-SR04 GND → GND
- HC-SR04 TRIG → Arduino digital pin (e.g., D2)
- HC-SR04 ECHO → Arduino digital pin (e.g., D3) — use voltage divider if needed for 5V tolerant boards

LCD (I2C) example:
- LCD SDA → A4 (on Uno)
- LCD SCL → A5
- LCD VCC → 5V
- LCD GND → GND

If using multiple sensors, assign distinct TRIG/ECHO pins for each sensor.

(Would be good to add a visual circuit diagram here — e.g., a Fritzing image.)

## Software
- Arduino IDE (1.8.x or 2.x) or PlatformIO
- Libraries (if using I2C LCD): `LiquidCrystal_I2C` or `LiquidCrystal` (for parallel)
- If using ultrasonic sensors, the code will measure distance and apply a threshold to determine occupancy.

## Installation & Upload
1. Install Arduino IDE: https://www.arduino.cc/en/software
2. Install any required libraries:
   - In Arduino IDE: Sketch → Include Library → Manage Libraries → search and install `LiquidCrystal_I2C` if needed.
3. Open the provided sketch file (e.g., `SmartParking.ino`) in the repo.
4. Connect your Arduino via USB.
5. Select the correct board and port in Tools → Board / Port.
6. Click Upload.

Example threshold logic:
- If measured distance < 20 cm → spot is occupied
- Else → spot is free

## Usage / Testing
- Power the system and place the sensors above parking spots.
- Walk or place an object near a spot to simulate a car; the display should update.
- Check serial monitor for debug messages (Tools → Serial Monitor at 9600 baud).

## Troubleshooting
- Sensor gives noisy readings: take median of several samples or apply smoothing.
- False positives: adjust threshold distance or sensor position/angle.
- LCD not showing text: check I2C address (commonly 0x27 or 0x3F) and wiring.
- HC-SR04 ECHO pin reading wrong: confirm wiring and add a 5V→5V safe connection.

## Screenshots
(Include photos of your breadboard and display here. Example:)
![Prototype photo](./assets/prototype.jpg)

## Contributing
Contributions are welcome. To propose changes:
1. Fork the repository
2. Create a branch (feature/my-change)
3. Open a pull request with a description of changes

Please include schematics, pictures, and tested code when contributing.

## License
This project is licensed under the MIT License — see the LICENSE file for details.

## Contact
Developed by Bhar-34.  
For questions: (add your preferred contact method — GitHub profile link or email).