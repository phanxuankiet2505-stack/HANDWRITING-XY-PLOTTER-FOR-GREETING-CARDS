# 3-Axis Automated Handwriting XY Plotter for Greeting Cards
Graduation Project
## 1. Project Overview
This repository contains the embedded firmware and web-based user interface for a **3-Axis Automated Handwriting XY Plotter** designed and built from scratch to automate greeting card writing.

### Key Hardware & Mechanical Highlights
* **Dual-Motor Y-Axis with Auto-Squaring:** Driven by **two synchronized stepper motors** (dual lead-screws) paired with **two independent limit switches (Y1 & Y2)** to perform automatic gantry squaring (dual homing), preventing mechanical racking and ensuring orthogonal accuracy.
* **X-Axis Positioning:** High-precision lead-screw drive transmission for smooth horizontal lettering.
* **Z-Axis Force Control:** Rack-and-pinion mechanism integrated with a **spring-loaded assembly** for passive contact force control—compensating for card surface unevenness and protecting the pen tip.
* **Custom Electronics:** Self-designed schematic and PCB integrating an **ESP32** microcontroller, **four stepper motor drivers** (`TMC2209`), four limit switches (X, Y1, Y2, Z), and power management circuits.
* **Wireless SD-Hosted Web UI:** Custom HTML/JS interface (`writer.html`) stored on a **microSD card** and served over ESP32 Wi-Fi for wireless text-to-G-code conversion, manual axis jogging, and real-time plotting status.

---

## 2. System Architecture & Data Flow
1. **Web Interface Hosting:** Upon startup, the ESP32 initializes the microSD card via **SPI** and runs an internal HTTP/WebSocket server over Wi-Fi.
2. **Path Generation:** Users access `writer.html` via a web browser, enter greeting card text, adjust layout parameters, and stream the generated G-code wirelessly to the controller.
3. **Motion Control & Auto-Squaring:** The customized `GRBL_Esp32-main` firmware parses G-code commands, executes dual-axis homing to square the Y-axis gantry, and generates real-time `STEP/DIR` pulses via hardware timer interrupts to synchronize all four stepper motors.

---

## 3. Repository Structure
```text
HANDWRITING-XY-PLOTTER-FOR-GREETING-CARDS/
├── Grbl_Esp32-main/      # Customized GRBL_Esp32-main motion control firmware
├── WebUI/                # Custom browser-based UI (writer.html) for microSD card
└── README.md             # Project documentation and setup guide
```
---

## 4. Images of machine
Image of PCB
<img width="754" height="603" alt="image" src="https://github.com/user-attachments/assets/0954a3c3-0951-43a2-bace-74e5367e777b" />
Image of the machine
<img width="720" height="1280" alt="image" src="https://github.com/user-attachments/assets/25d3e8e7-79c3-4958-91b8-64469bf06dd3" />
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/62d4824d-eba3-4eeb-9f58-57c3f409730f" />
<img width="720" height="1280" alt="image" src="https://github.com/user-attachments/assets/ec5843de-02c8-434e-b964-d64b23811a94" />




