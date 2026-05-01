# Steering Board
**Squadra Corse PoliTo — Formula Student (Season SC26)**

[![Hardware](https://img.shields.io/badge/Hardware-PCB_Design-blue)](#)
[![Microcontroller](https://img.shields.io/badge/MCU-STM32F446-orange)](#)
[![Status](https://img.shields.io/badge/Status-Manufactured_&_Tested-brightgreen)](#)

## 🏎️ System Overview

This repository contains the hardware design for the Steering Board electronics, a central node that serves as the primary physical interface for the driver during race conditions. 

Powered via a 5V line from the main Dashboard, this board captures critical driver inputs—such as Torque Vectoring, Traction Control, and Launch Control toggles—and securely transmits them to the rest of the vehicle via the CAN bus protocol. The system was specifically engineered to update legacy designs while preparing the vehicle architecture for the upcoming driverless/autonomous transition.

## ✨ Key Features & Hardware Specifications

* **Microcontroller:** STM32F446RET6TR, responsible for input acquisition and CAN transmission.
* **Driver Inputs:** 
  * 5x independent Push Buttons (Torque Vectoring, Traction Control, Launch Control, and General mapping).
  * 3x 10-Position Rotary Switches.
* **Communication:** Standard CAN bus interface for reliable, noise-immune telemetry.
* **Power Supply:** 5V input directly fed from the Dashboard ECU.

## 🧠 Subsystem Engineering & Design Highlights

### 1. Flexible Mechanical Integration
Because the final ergonomic placement of buttons on a custom carbon-fiber steering wheel often changes late in the design cycle, the push buttons were deliberately not hardcoded/soldered directly to the main PCB. Instead, the board utilizes waterproof Molex connectors to allow for modular harnesses, granting the mechanical team complete freedom over the final button positioning.

### 2. Driverless Transition & Debugging Matrix
To future-proof the design for the team's transition to autonomous racing, the PCB incorporates a dedicated development and debugging area. Every pin of the STM32 microcontroller is routed to a through-hole prototyping matrix on the board itself. This allows software and hardware engineers to easily probe pins, tap into signals, or add modular jump-wires during the autonomous transition without requiring a completely new PCB spin.

### 3. Hardware Signal Conditioning
In an electrically noisy racing environment, raw mechanical switch inputs cannot be trusted. All incoming signals from the rotary switches and push buttons are routed through dedicated hardware conditioning circuits before reaching the MCU, ensuring perfectly clean logic transitions.

## 📁 Repository Structure
```text
├── Gerbers/                            # Production files for manufacturing
├── BOM/                                # Bill of Materials
├── Schematics/                         # PDF exports of the circuit design
├── Step/                               # 3D Model of the board for mechanical packaging
├── Steering_v2_Wiki_Specification.pdf  # System and Subsystem Specification Document
└── README.md
