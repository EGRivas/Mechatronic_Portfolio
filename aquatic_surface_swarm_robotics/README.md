# Undergraduate Thesis Project: Autonomous Surface Swarm Robotics for Environmental Monitoring

[![ROS 2](https://img.shields.io/badge/ROS_2-Jazzy_Jalisco-blue.svg)](https://docs.ros.org/en/jazzy/)
[![Gazebo](https://img.shields.io/badge/Gazebo-Harmonic-orange.svg)](https://gazebosim.org/)
[![SBC](https://img.shields.io/badge/SBC-Raspberry_Pi_Zero_2_W-C51A4A.svg?logo=raspberrypi&logoColor=white)](https://www.raspberrypi.com/)
[![MCU](https://img.shields.io/badge/MCU-ESP32-E7352C.svg?logo=espressif&logoColor=white)](https://www.espressif.com/)
[![Protocol](https://img.shields.io/badge/Comms-ESP--NOW_Ad--Hoc-009688.svg)](https://www.espressif.com/)
[![Status](https://img.shields.io/badge/Status-Field_Validated_%7C_Q1_Under_Review-success.svg)](#research--publications)

An end-to-end decentralized swarm of **Unmanned Surface Vehicles (USVs)** engineered for continuous spatial-temporal water quality assessment (pH and temperature). The system eliminates the need for human boat operators and cellular infrastructure by combining high-fidelity **hydrodynamic simulation in ROS 2 / Gazebo Harmonic**, distributed peer-to-peer ad-hoc communication and physical multi-agent field deployments.

Developed at **CoRAL Lab (ESPOL)**.

---

## 🎬 Field Deployments & Sim-to-Real Showcase

| Physical Deployment (ESPOL Lake) | Hydrodynamic Swarm Simulation (Gazebo) |
| :---: | :---: |
| ![Physical Swarm Fleet](media/fleet_lake_espol.gif) | ![Gazebo 20-Robot Simulation](media/gazebo_swarm_simulation.gif) |
| *3 USVs executing decentralized waypoint patrol* | *Multi-agent scalability testing (up to 20 concurrent nodes)* |

> 📺 **Full Video Demonstrations:**  
> - 🇪🇨 & 🇪🇸 [Watch 3-Agent Autonomous Missions and brief explanation (YouTube)](https://youtu.be/TU_VIDEO_ESPOL)  
> - 🏊 [Watch Simulation Development Tests (YouTube playlist)](https://youtu.be/TU_VIDEO_POOL)
> - | *All missions were made in real enviroments such as lakes (ESPOL and UAM) and pools* |

---

## 📌 System Architecture

The USV platform is built upon a hybrid distributed embedded architecture, separating high-level autonomous navigation from real-time data acquisition and peer-to-peer networking.

ARCHITECTURE IMAGE

### 1. High-Level Navigation (Raspberry Pi Zero 2 W)
* Executes path tracking, mission state machines and ROS 2 nodes (in actual development) under an embedded Linux environment.
* Translates target geographic waypoints into continuous heading and thrust setpoints.
* Generates PWM signals for **APISQUEEN underwater thrusters**, incorporating immediate emergency cut-offs.

### 2. Low-Level Control & Ad-Hoc Mesh (ESP32)
* Interacts directly with hardware: analog/digital front-ends for industrial-grade pH and temperature probes.
* Runs IMU yaw estimation and GPS positioning.
* Hosts the decentralized **ESP-NOW communication protocol**, maintaining dynamic neighbor tables without reliance on local Wi-Fi routers or 4G/5G towers.

---

## ⚡ Core Engineering Capabilities

### 1. Decentralized Coordination & ESP-NOW Mesh
* Nodes broadcast local coordinates, heading and velocity vectors at periodic intervals.
* The swarm autonomously segments large bodies of water without central server orchestration.
* When two agents detect converging trajectories within safety radius, reactive decentralized collision avoidance policies adjust thruster differentials deterministically.

### 2. Sim-to-Real Transfer (ROS 2 Jazzy + Gazebo Harmonic)
* Modeled full rigid-body hydrodynamics (buoyancy, drag tensors, hydrodynamic damping in actual development) using URDF.
* Tested different types of swarm control algorithms. Proprietary algorithm based on 2D BOIDS (still not implemented on real scenarios) and waypoint based algorithms (tested on real environments as shown on videos) .
* Scaled multi-robot mission scenarios up to **20 simultaneous agents** in simulation prior to manufacturing.

![Gazebo Multi-Agent Setup](media/gazebo_architecture.png)

### 3. Continuous Water Quality Telemetry
* Instead of discrete, single-point water samples, the vehicles compile spatial-temporal time-series datasets.
* Real-time field telemetry (pH, °C, GPS position, and timestamps) is streamed to an operational **Node-RED supervision dashboard**.

![Node-RED Monitoring Dashboard](media/dashboard_nodered.png)

---

## 📊 Technical Specifications

| Parameter | Specification | Details |
| :--- | :--- | :--- |
| **Swarm Size** | 3 Physical Units (Scalable) | Simulated up to 20 nodes in Gazebo Harmonic |
| **Primary Compute (SBC)** | Raspberry Pi Zero 2 W | Quad-core ARM Cortex-A53 @ 1 GHz, 512MB RAM |
| **Real-Time MCU** | ESP32-WROOM-32 | Dual-core Tensilica Xtensa 32-bit @ 240 MHz |
| **Inter-Agent Comms** | ESP-NOW (2.4 GHz) | Peer-to-peer ad-hoc packet delivery with zero network infrastructure |
| **Sensors** | GPS, IMU, pH, Temp | Continuous time-series data acquisition |
| **Propulsion** | APISQUEEN Underwater Thrusters | Differential thrust configuration for holonomic surface rotation |
| **Power Supply** | 3S LiPo (11.1V, High Capacity) | ~9 hours continuous autonomous mission endurance |
| **Chassis & Enclosure** | Hybrid Annular Float + 3D Core | Waterproof IP67 custom enclosure, modular maintenance access |
| **Unit Manufacturing Cost**| ~$600 USD per node | Cost-effective alternative to commercial single-vessel buoys |

---

## 🗺️ Real-World Application Domains

* **Industrial Aquaculture & Shrimp Farms:** Continuous monitoring of pH stratification and critical temperature shifts across multi-hectare ponds without operational boat crews.
* **Estuaries, Rivers & Reservoirs:** Early detection of industrial effluent discharges and ecological boundary tracking.
* **Academic Multi-Agent Research:** Accessible, modular hardware platform for distributed consensus algorithms, Voronoi tessellation coverage, and cooperative path planning.

---

## 📁 Repository Structure

```text
aquatic_surface_swarm_robotics/
├── README.md                           # Project case study (this file)
├── README.es.md                        # Versión en español del estudio de caso
├── media/                              # Visual assets, telemetry plots, and schematics
│   ├── fleet_lake_espol.gif            # 3 USVs operating in ESPOL Lake
│   ├── gazebo_swarm_simulation.gif     # agent simulation demonstration
│   ├── dashboard_nodered.png           # Live Node-RED dashboard interface
│   └── hardware_chassis_render.png     # SolidWorks 3D CAD explode / physical build
```

---

## 🔒 Research & Intellectual Property Notice
> **Note on Research Data & Source Code:**  
> The complete algorithmic implementation (decentralized consensus, hydrodynamic and control parameter tuning) along with full experimental datasets are part of an ongoing manuscript currently prepared for submission to a Q1-indexed peer-reviewed journal. Full source code access is available upon request for academic evaluation or technical hiring committees.

---

## 👤 Research & Development Team

* **Emmanuel Rivas Pincay** — Robotics, Embedded Systems, Experimental Validation & Simulation Engineer  
  *Mechatronics Engineering Graduate, ESPOL*  
  [LinkedIn](https://linkedin.com/in/emmanuel-rivas-pincay-a25334221) | [Email](mailto:egrivas64@gmail.com)

* **Milena Rodríguez Astudillo** — Robotics, Mechanical Design & Experimental Validation Engineer  
  *Mechatronics Engineering Graduate, ESPOL*  
  [LinkedIn](https://www.linkedin.com/in/milena-dayanna-rodr%C3%ADguez-astudillo-4976b4298/) | [Email](mailto:mildarod@espol.edu.ec)

### 🏛️ Academic Affiliation & Supervision
* ** Thesis Advisors:** [David Garzón, Ph.D.](https://scholar.google.com/citations?user=4-CJclQAAAAJ&hl=en) | [Christian Tutivén, Ph.D.](https://scholar.google.com/citations?hl=en&user=yN1sEhsAAAAJ) 
* **Research Group:** **CoRAL** (Collective Robotics and AI Lab)
* **Institution:** Escuela Superior Politécnica del Litoral (ESPOL), Guayaquil, Ecuador
