# Proyecto de Tesis de Grado: Robótica de Enjambre Acuática de Superficie para Monitoreo Ambiental

[![ROS 2](https://img.shields.io/badge/ROS_2-Jazzy_Jalisco-blue.svg)](https://docs.ros.org/en/jazzy/)
[![Gazebo](https://img.shields.io/badge/Gazebo-Harmonic-orange.svg)](https://gazebosim.org/)
[![SBC](https://img.shields.io/badge/SBC-Raspberry_Pi_Zero_2_W-C51A4A.svg?logo=raspberrypi&logoColor=white)](https://www.raspberrypi.com/)
[![MCU](https://img.shields.io/badge/MCU-ESP32-E7352C.svg?logo=espressif&logoColor=white)](https://www.espressif.com/)
[![Protocol](https://img.shields.io/badge/Comms-ESP--NOW_Ad--Hoc-009688.svg)](https://www.espressif.com/)
[![Status](https://img.shields.io/badge/Estado-Validado_en_Campo_%7C_En_Revisi%C3%B3n_Q1-success.svg)](#aviso-de-investigación-y-propiedad-intelectual)

Un enjambre descentralizado de extremo a extremo de **Vehículos de Superficie No Tripulados (USV, por sus siglas en inglés)** diseñado para la evaluación espaciotemporal continua de la calidad del agua (pH y temperatura). El sistema elimina la necesidad de operadores humanos en botes y de infraestructura de red celular al combinar **simulación en ROS 2 / Gazebo Harmonic**, comunicación ad-hoc peer-to-peer distribuida y despliegues físicos multiagente en campo.

Desarrollado en **CoRAL Lab (ESPOL)**.

---

## 🎬 Despliegues en Campo y Demostración Sim-to-Real

### Despliegue Físico (Lago ESPOL)
<p align="center">
  <img src="media/fleet_lake_espol.gif" width="320" alt="Flota de Enjambre Físico">
  <br>
  <em>Pruebas en lago con los 3 USVs</em>
</p>

### Simulación Hidrodinámica de Enjambre (Gazebo)
<p align="center">
  <img src="media/gazebo_swarm_simulation.gif" width="720" alt="Simulación de 20 Robots en Gazebo">
  <br>
  <em>Pruebas de escalabilidad multiagente (hasta 20 nodos concurrentes)</em>
</p>

> 📺 **Demostraciones en Video Completas:**  
> - 🇪🇨 & 🇪🇸 [Ver pruebas con los 3 agentes construidos y explicación breve del proyecto (YouTube)](https://youtu.be/UMnkEa_evzY)  
> - 🏊 [Ver pruebas de desarrollo de la simulación (Lista de reproducción en YouTube)](https://youtube.com/playlist?list=PL8n_4KnNGx2n-5VLmENLNj3OTQICQIQzr&si=vs_kWSMrW3dEg3GG)  
> - 🏊 [Ver publicación de la facultad universitaria sobre este proyecto (Reel de Instagram)](https://www.instagram.com/reel/DceYdwiy3MX/?mdxt=MzRlODBiNWFlZA==)  
> - *Todas las misiones fueron realizadas en entornos reales como lagos (ESPOL y UAM) y piscinas.*

---

## 📌 Arquitectura del Sistema

La plataforma USV está construida sobre una arquitectura embebida distribuida híbrida, separando la navegación autónoma de alto nivel de la adquisición de datos en tiempo real y la red peer-to-peer.

### 1. Navegación de Alto Nivel (Raspberry Pi Zero 2 W)
- Ejecuta el seguimiento de trayectorias, máquinas de estados de misión y nodos de ROS 2 (en desarrollo actual) bajo un entorno Linux embebido.
- Traduce los waypoints geográficos objetivo en consignas continuas de rumbo y empuje.
- Genera señales PWM para los **propulsores subacuáticos APISQUEEN**, incorporando cortes de emergencia inmediatos.

### 2. Control de Bajo Nivel y Malla Ad-Hoc (ESP32)
- Interactúa directamente con el hardware: etapas front-end analógicas/digitales para sondas de pH y temperatura de grado industrial.
- Ejecuta la estimación de orientación (yaw) mediante IMU y posicionamiento GPS.
- Aloja el **protocolo de comunicación descentralizado ESP-NOW**, manteniendo tablas dinámicas de vecinos sin depender de routers Wi-Fi locales ni torres 4G/5G.

<p align="center">
  <img src="media/dual_architecture.png" width="720" alt="Arquitectura Dual">
  <br>
  <em>Figura 1: Arquitectura embebida híbrida hardware-software de la plataforma de enjambre acuático.</em>
</p>

---

## ⚡ Capacidades Principales de Ingeniería

### 1. Coordinación Descentralizada y Malla ESP-NOW
- Los nodos transmiten coordenadas locales, vectores de rumbo y velocidad a intervalos periódicos.
- El enjambre segmenta de forma autónoma grandes masas de agua sin la orquestación de un servidor central.
- Cuando dos agentes detectan trayectorias convergentes dentro de un radio de seguridad, políticas reactivas y descentralizadas de evasión de colisiones ajustan el empuje diferencial de manera determinista.

### 2. Transferencia Sim-to-Real (ROS 2 Jazzy + Gazebo Harmonic)
- Modelado hidrodinámico completo de cuerpo rígido (flotabilidad, arrastre y amortiguamiento hidrodinámico en desarrollo actual) utilizando URDF y plugins de Gazebo.
- Pruebas de diferentes algoritmos de control de enjambre: algoritmo propietario basado en BOIDS 2D (aún no implementado en escenarios reales) y algoritmos basados en waypoints (probados en entornos reales como se muestra en los videos).
- Escalado de escenarios de misiones multi-robot hasta **20 agentes simultáneos** en simulación previo a la manufactura física.

<p align="center">
  <img src="media/gazebo_architecture.png" width="460" alt="Configuración Multiagente en Gazebo">
  <br>
  <em>Figura 2: ROS 2 / Gazebo Harmonic y arquitectura de despliegues multiagente.</em>
</p>

### 3. Telemetría Continua de Calidad del Agua
- En lugar de muestras de agua discretas y de un solo punto, los vehículos compilan conjuntos de datos de series temporales espaciotemporales.
- La telemetría de campo en tiempo real (pH, °C, posición GPS y marcas de tiempo) se transmite a un **panel de supervisión operativa en Node-RED**.

<p align="center">
  <img src="media/dashboard_nodered.png" width="460" alt="Panel de Monitoreo en Node-RED">
  <br>
  <em>Figura 3: Dashboard operativa en tiempo real, visualización de trayectorias GPS y monitoreo ambiental.</em>
</p>

---

## 📊 Especificaciones Técnicas

| Parámetro | Especificación | Detalles |
| :--- | :--- | :--- |
| **Tamaño del Enjambre** | 3 Unidades Físicas (Escalable) | Simulación de hasta 20 nodos en Gazebo Harmonic |
| **Cómputo Principal (SBC)** | Raspberry Pi Zero 2 W | Quad-core ARM Cortex-A53 @ 1 GHz, 512MB RAM |
| **MCU de Tiempo Real** | ESP32-WROOM-32 | Dual-core Tensilica Xtensa 32-bit @ 240 MHz |
| **Comunicaciones Inter-Agente** | ESP-NOW (2.4 GHz) | Entrega de paquetes ad-hoc peer-to-peer con cero infraestructura de red |
| **Sensores** | GPS, IMU, pH, Temperatura | Adquisición continua de datos en series temporales |
| **Propulsión** | Propulsores Subacuáticos APISQUEEN | Configuración de empuje diferencial para rotación holonómica en superficie |
| **Alimentación / Batería** | LiPo 3S (11.1V, Alta Capacidad) | ~9 horas de autonomía en misión continua autónoma |
| **Chasis y Carcasa** | Flotador Anular Híbrido + Núcleo 3D | Carcasa personalizada impermeable IP67, acceso modular para mantenimiento |
| **Costo de Manufactura por Unidad** | ~$600 USD por nodo | Alternativa costo-efectiva frente a boyas comerciales de un solo vehículo |

---

## 🗺️ Campos de Aplicación en el Mundo Real

- **Investigación Académica Multiagente:** Plataforma de hardware accesible y modular para algoritmos de consenso distribuido, cobertura por teselación de Voronoi y planificación cooperativa de trayectorias.
- **Acuicultura Industrial y Camaroneras:** Monitoreo continuo de la estratificación del pH y cambios críticos de temperatura en piscinas de múltiples hectáreas sin requerir personal en botes.
- **Estuarios, Ríos y Embalses:** Detección temprana de descargas de efluentes industriales y seguimiento de límites ecológicos.

---

## 📁 Estructura del Repositorio

```text
aquatic_surface_swarm_robotics/
├── README.md                           # Estudio de caso del proyecto (en inglés)
├── README.es.md                        # Versión en español del estudio de caso (este archivo)
├── media/                              # Recursos visuales, gráficos de telemetría y esquemáticos
│   ├── fleet_lake_espol.gif            # 3 USVs operando en el Lago ESPOL
│   ├── dual_architecture.png           # Arquitectura dual del sistema de enjambre acuático
│   ├── gazebo_swarm_simulation.gif     # Demostración de simulación con agentes
│   ├── dashboard_nodered.png           # Interfaz del panel de monitoreo en Node-RED en vivo
│   ├── hardware_chassis_render.png     # Vista explosionada CAD 3D en SolidWorks
│   ├── physical_connections.jpg        # Conexiones electrónicas reales
│   └── pcb_design.jpg                  # PCB diseñada en KiCad, extensión de pines ESP32
```

---

## 🔒 Research & Intellectual Property Notice
> **Sobre los Datos de Investigación y Código Fuente:**  
> La implementación algorítmica completa (consenso descentralizado, ajuste de parámetros hidrodinámicos y de control), junto con los sets completos de datos experimentales, forman parte de un manuscrito en preparación para su envío a una revista científica indexada Q1. El acceso completo al código fuente está disponible bajo solicitud para evaluación académica o comités técnicos de contratación.

---

## 👤 Equipo de Investigación y Desarrollo

* **Emmanuel Rivas Pincay** — Ingeniero en Robótica, Sistemas Embebidos, Validación Experimental y Simulación  
  *Graduado en Ingeniería Mecatrónica, ESPOL*  
  [LinkedIn](https://linkedin.com/in/emmanuel-rivas-pincay-a25334221) | [Email](mailto:egrivas64@gmail.com)

* **Milena Rodríguez Astudillo** — Ingeniera en Robótica, Diseño Mecánico y Validación Experimental  
  *Graduada en Ingeniería Mecatrónica, ESPOL*  
  [LinkedIn](https://www.linkedin.com/in/milena-dayanna-rodr%C3%ADguez-astudillo-4976b4298/) | [Email](mailto:mildarod@espol.edu.ec)

### 🏛️ Afiliación Académica y Dirección de Tesis
* **Directores de Tesis:** [David Garzón, Ph.D.](https://scholar.google.com/citations?user=4-CJclQAAAAJ&hl=en) | [Christian Tutivén, Ph.D.](https://scholar.google.com/citations?hl=en&user=yN1sEhsAAAAJ) 
* **Grupo de Investigación:** **[CoRAL](https://github.com/coral-espol/)** (Collective Robotics and AI Lab)
* **Institución:** Escuela Superior Politécnica del Litoral (ESPOL), Guayaquil, Ecuador
