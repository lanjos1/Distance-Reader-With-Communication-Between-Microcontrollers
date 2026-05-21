# Distance Reader with Communication Between Microcontrollers

[![Watch the Video](https://img.shields.io/badge/YouTube-Project_Video-red?logo=youtube)](https://youtu.be/DNFJZB2kEZk)
[![Tinkercad Simulation](https://img.shields.io/badge/Tinkercad-System_Simulation-blue)](https://www.tinkercad.com/things/3Du9q5At9HA-distance-reader-with-communication-between-microcontrollers)

This project establishes a robust embedded ecosystem consisting of two **Arduino UNO** microcontrollers communicating over a Master-Slave architecture via **Serial Communication**. The system acts as an automated smart distance reader, utilizing an ultrasonic sensor to monitor distances, processing the logic on a Master node, and transmitting specific actions, system states, and telemetry data to a Slave node for physical user feedback.

<div align="center">
  <img src="images/esquema-arduino.png" width="600" alt="System Circuit Layout"/>
</div>

## 🚀 System Architecture & Features
* **Master-Slave Serial Network:** High-fidelity serial communication to synchronize data streams between isolated microcontrollers.
* **Ultrasonic Distance Tracking:** Accurate, real-time spatial awareness powered by the HC-SR04 sensor connected to the Master node.
* **Multilevel Visual Signaling:** A dynamic 3-LED status system (Blue, Yellow, Red) driven by the Slave node representing safe, warning, and critical proximity zones.
* **Intelligent Telemetry Dashboard:** A liquid-crystal display (16x2 LCD) on the Slave end presenting contextual user text based on real-time distance data.
* **Brightness/Contrast Control:** Integrated analog potentiometer dedicated to physically tuning the display contrast and text legibility.

## 🛠️ Technical Specifications (Components)

### Hardware Components
* **2x Microcontrollers:** Arduino UNO R3 (1x Master, 1x Slave).
* **1x Ultrasonic Sensor:** HC-SR04 (Distance detection module).
* **1x LCD Display:** 16x2 Liquid Crystal Display (Output character monitor).
* **1x Potentiometer:** Used for fine-tuning the contrast and visibility of the LCD screen.
* **3x LEDs:** Diagnostic indicators (1x Blue, 1x Yellow, 1x Red).
* **3x Resistors:** 220 Ω resistors for current-limiting LED protection.
* **2x Protoboards:** For component placement and power rail distribution.
* **32x Jumper Wires:** M-M / M-F serial interconnects.

### Software & Tools
* **Arduino IDE:** Used for developing and compiling embedded C++ code for both independent firmwares.
* **Proteus / TinkerCAD:** Used for schematic capture, circuit design, and simulation validation.
* **GitHub:** Repository hosting and code versioning.

## 🔌 Communication & Interconnection Protocol

The master node processes sensor loops and converts threshold rules into structural packet payloads transmitted through hardware serial ports (`TX`/`RX`).

### Wiring Overview
* **Master TX (Pin 1)** ➡️ **Slave RX (Pin 0)**
* **Common Ground:** Both Arduinos share a common `GND` rail to synchronize logic voltage reference levels.

### Pinout Mapping
* **HC-SR04 (Master):** `Trigger` mapped to Digital Pin 7; `Echo` mapped to Digital Pin 6.
* **LED Status Matrix (Slave):** Blue (Safe), Yellow (Warning), and Red (Critical Danger) connected to designated digital outputs with 220 Ω resistors.
* **LCD Display (Slave):** Wired using standard parallel interface pins (`RS`, `E`, `D4`, `D5`, `D6`, `D7`) to monitor incoming buffer text.
* **Potentiometer (Slave):** Wired to the contrast control pin (`V0`) of the LCD display to adjust character visibility.

## 🎮 How to Setup and Run

1. **Hardware Assembly:** Assemble the circuit components onto your protoboards following the system schematic layout (`images/esquema-arduino.png`) or use the online [TinkerCAD Simulation](https://www.tinkercad.com/things/3Du9q5At9HA-distance-reader-with-communication-between-microcontrollers). Ensure both Arduino boards share a single unified Ground (`GND`).
2. **Flash the Master Firmware:** Open the Master node source code in the Arduino IDE and upload it to the designated transmitting Arduino.
3. **Flash the Slave Firmware:** Disconnect the `RX`/`TX` cross-wires temporarily, open the Slave node source code, and upload it to the receiving Arduino.
4. **Initialize System:** Reconnect the serial communication data lines (`TX` to `RX`), power up both microcontrollers via USB or an external DC source, and observe real-time distance calculations and status feedback.

---
Developed as a practical laboratory application for Embedded Systems engineering.
