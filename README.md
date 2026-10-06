# Emmanuel Rivas Pincay — Mechatronics & Robotics Portfolio

[![ROS 2](https://img.shields.io/badge/ROS_2-Jazzy_Jalisco-blue.svg)](https://docs.ros.org/en/jazzy/)
[![Gazebo](https://img.shields.io/badge/Gazebo-Harmonic-orange.svg)](https://gazebosim.org/)
[![C++](https://img.shields.io/badge/C++-17%2F20-00599C.svg?logo=c%2B%2B)](https://isocpp.org/)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB.svg?logo=python)](https://www.python.org/)
[![Raspberry Pi](https://img.shields.io/badge/SBC-Raspberry_Pi_Zero_2_W-C51A4A.svg?logo=raspberrypi&logoColor=white)](https://www.raspberrypi.com/)
[![Embedded](https://img.shields.io/badge/Platform-ESP32%20%7C%20Linux-red.svg)](https://www.espressif.com/)
[![License: Academic / Open](https://img.shields.io/badge/Access-Research%20Showcase-green.svg)](#intellectual-property--code-access)

Mechatronics Engineer graduated from **ESPOL** (Guayaquil, Ecuador) specializing in **autonomous robotics, embedded systems, and distributed control architectures**. 

This repository serves as a centralized technical showcase of my major engineering and research projects, focusing on end-to-end system ownership: mathematical modeling, simulation (sim-to-real), PCB & CAD design, embedded firmware, software and hardware integration.

---

## 🧰 Core Engineering Skills

* **Robotics & Simulation:** ROS 2 (Jazzy), Gazebo (Harmonic), URDF/xacro, TF2, Waypoint Navigation, Kinematics & Dynamics, Hydrodynamic Modeling.
* **Languages & Frameworks:** C++, Python, C, Java (OOP), Linux/Ubuntu (CLI, Bash, Git), TensorFlow / Keras (1D-CNNs).
* **Control & Mathematics:** Digital PID Tuning, State-Space Representation, Transfer Functions, Sensor Filtering (IMU & GPS), Collision Avoidance.
* **Embedded Systems & Hardware:** Raspberry Pi Zero 2 W (Linux SBC), ESP32, ATmega, FreeRTOS, KiCad PCB Design, ESP-NOW, BLE, UART, I2C, SPI.
* **Industrial Automation:** Siemens S7 PLCs (S7-300, S7-1200, S7-1500), TIA Portal, HMI, VFDs (Delta), Servodrives (Yaskawa), P&ID Instrumentation.

---

## 🧭 Featured Projects Overview

| Project | Domain | Core Stack | Key Highlights | Case Study |
| :--- | :--- | :--- | :--- | :---: |
| **Aquatic Surface Swarm Robotics** | Autonomous USVs / Multi-Agent | ROS 2, Gazebo Harmonic, Raspberry Pi, Python, ESP32, C++, ESP-NOW | Lake-tested fleet of 3 ASVs; simulation scaled to 20 agents; decentralized collision avoidance. | [Explore ➔](./aquatic_surface_swarm_robotics/) |
| **Biomechatronic Fall Detection** | Applied ML & Edge Telemetry | Python, 1D-CNN, ESP32, BLE | Real-time inertial time-series classification; low-latency edge-to-mobile alert pipeline. | [Explore ➔](./biomechatronic_fall_detection/) |
| **Cobot & Pneumatic Integration** | Industrial Automation | UFACTORY Lite 6, Festo, ESP32, Node-RED | Legacy-to-smart pneumatic cell sequencing; IoT telemetry bridge; Real time monitoring. | [Explore ➔](./ufactory_festo_integration/) |
| **Modular Open-Source PLC** | Embedded Systems & Hardware | KiCad, ESP32, C++, FreeRTOS | Custom modular PCB architecture; isolated industrial I/O; dual Ladder & C++ runtime. | [Explore ➔](./modular_opensource_plc/) |

---

## 🛠️ Project Showcases

### 1. [Decentralized Swarm of Aquatic Surface Vehicles (USVs)](./aquatic_surface_swarm_robotics/)
> **Keywords:** Unmanned Surface Vehicles, ROS 2 Jazzy, Gazebo Harmonic, ESP-NOW, Decentralized Flocking.

* **Objective:** Design, build, and deploy an autonomous fleet of 3 USVs for distributed water-quality monitoring (pH, temperature) in real aquatic environments.
* **Architecture & Simulation:** Developed high-fidelity hydrodynamic simulations in **Gazebo Harmonic + ROS 2 Jazzy** supporting up to 20 concurrent agents before field deployment.
* **Control & Comms:** Integrated GPS waypoint navigation, IMU orientation tracking and decentralized peer-to-peer collision avoidance using the **ESP-NOW** protocol.
* **Validation:** Validated in open water at the ESPOL lake, logging timestamped trajectories and telemetry through a centralized Node-RED dashboard.
* 🔗 **[Read the Full Case Study & View Lake Validation Demos ➔](./aquatic_surface_swarm_robotics/)**

---

### 2. [Biomechatronic Fall Detection System with Edge ML](./biomechatronic_fall_detection/)
> **Keywords:** 1D-CNN, Wearable IoT, BLE, ESP32, Time-Series Classification.

* **Objective:** Real-time human activity recognition (HAR) and emergency fall detection using compact wearable inertial sensors.
* **Pipeline:** Designed and trained a **1D Convolutional Neural Networks (1D-CNN)** in Python for feature extraction on multivariate accelerometer and gyroscope time-series data.
* **Embedded Telemetry:** Deployed an ESP32 edge node streaming motion frames over **Bluetooth Low Energy (BLE)** to an inference backend server connected to a mobile alert client.
* 🔗 **[Read the Full Case Study & View Confusion Matrix & Architecture ➔](./biomechatronic_fall_detection/)**

---

### 3. [Collaborative Robot Integration with Festo Pneumatics](./ufactory_festo_integration/)
> **Keywords:** UFACTORY Lite 6, Festo Didactic, Industrial IoT, State Machines, Node-RED.

* **Objective:** Improve an industrial didactic distribution cell by retrofitting a 6-DOF collaborative manipulator with legacy pneumatic actuators.
* **Integration Strategy:** Bridged sensor states from Festo pneumatic stations into the robotic trajectory planner using an intermediate microcontroller interface, bypassing costly PLC replacements.
* **Supervision:** Engineered an operational dashboard in Node-RED for real-time cycle status, part counting, and fault diagnostics.
* 🔗 **[Read the Full Case Study & View Cell Sequencing Demos ➔](./ufactory_festo_integration/)**

---

### 4. [Modular Open-Source Industrial PLC](./modular_opensource_plc/)
> **Keywords:** KiCad PCB Design, ESP32, Industrial I/O, Optocouplers, C++, Ladder Logic.

* **Objective:** Create a modular, cost-effective programmable logic controller for industrial education and light-automation deployments.
* **Hardware Design:** Engineered schematics and PCB layouts in **KiCad** featuring optically isolated digital inputs/outputs, 4–20mA analog channels, and power conditioning.
* **Firmware:** Developed a modular C++ runtime supporting native FreeRTOS tasks (standard Ladder logic in develompent).
* 🔗 **[Read the Full Case Study & View PCB Schematics & Renders ➔](./modular_opensource_plc/)**

---

## 🔒 Intellectual Property & Code Access

> **Note on Research Data & Source Code:**  
> Detailed architecture runbooks, system schematics, and simulation demonstrations are shared within each project folder. Full source code access is available upon request for academic evaluation or technical hiring committees.

---

## 📬 Contact & Links

* **Location:** Guayaquil, Ecuador
* **Email:** [egrivas64@gmail.com](mailto:egrivas64@gmail.com)
* **LinkedIn:** [linkedin.com/in/emmanuel-rivas-pincay-a25334221](https://linkedin.com/in/emmanuel-rivas-pincay-a25334221)
