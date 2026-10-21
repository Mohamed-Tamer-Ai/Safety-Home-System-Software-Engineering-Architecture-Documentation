# 🏠 Safety Home System | Software Engineering & Architecture Documentation

[![Platform](https://img.shields.io/badge/Hardware-ESP32%20%7C%20Sensors%20%7C%20Relays-blue)](#)
[![IoT](https://img.shields.io/badge/IoT%20Platform-Blynk%20Cloud-00C7B7)](#)
[![Language](https://img.shields.io/badge/Firmware-Arduino%20C%2B%2B-00599C)](#)
[![Course](https://img.shields.io/badge/Course-Software%20Engineering%20(FCAI--BU)-orange)](#)

> **Safety Home** is a safety-critical IoT and Embedded Software System designed for homes and facilities to provide early detection and automated response against combustible gas leaks, smoke, sudden temperature spikes, and direct flames.

🔗 **Live Product Landing Page:** [Safety Home Web Portal](https://github.com/mooaz-ebrahiem/safety_home)  
📸 **Official Instagram Page:** [@safety.home.eg](https://www.instagram.com/safety.home.eg/)

---

## 📌 1. Project Overview (نظرة عامة على المشروع)

When software directly controls physical hardware in a **Smart Home**, defects can impact human safety, cost, and trust. Therefore, **Safety Home** is engineered using a **systematic, disciplined, and quantifiable** Software Engineering approach.

The system continuously monitors the environment in real time. Upon detecting a hazard, it executes an immediate local fail-safe protocol (cutting off the gas valve and kitchen electrical outlets to prevent sparks while **keeping primary lighting active** for safe evacuation) and alerts the homeowner remotely via the **Blynk IoT App** with one-click access to emergency services.

---

## ✨ 2. Key System Features (المميزات الرئيسية)

* **🔥 Multi-Hazard Early Detection:**
  * **Gas & Smoke Monitoring:** Continuous sensing of LPG, methane, natural gas, and smoke using MQ-series sensors.
  * **Direct Flame Detection:** Instant optical detection of fire outbreaks.
  * **Thermal Spike Detection:** Monitoring rapid, abnormal increases in ambient temperature (via DHT sensors) before fire spreads.
* **⚡ Smart & Safe Power Management (Fail-Safe Action):**
  * Automatically disconnects kitchen appliances and power sockets via relays during a gas leak to prevent electrical sparks.
  * **Evacuation Lighting Exception:** Intentionally keeps the main room lighting circuit powered so residents can see and evacuate safely.
  * Automatically closes the mechanical gas solenoid valve.
* **🔊 Dual Local Alerting:** Activates a high-decibel **Buzzer** and visual **LED** indicators immediately on-site.
* **📱 IoT Mobile Integration & Emergency Dispatch (via Blynk):**
  * Real-time live sensor telemetry on the user's smartphone.
  * Instant **Push Notifications** when thresholds are breached.
  * **Manual Override:** Remote control to shut off valves or reset the system.
  * **One-Click Emergency Call:** Direct in-app shortcut to call Civil Defense (Fire Department / Ambulance).

---

## 🏗️ 3. Hardware & Software Architecture (البنية المعمارية)

Following the standard **Safety-Critical Embedded Architecture** (`Sensor ➔ Controller ➔ Actuator / Alarm / Display`):

### 🔧 Hardware Components
1. **Controller:** `ESP32` Microcontroller (Built-in Wi-Fi & Bluetooth).
2. **Sensors:**
   * `MQ-2 / MQ-5` Gas & Smoke Sensor.
   * `IR Flame Sensor` for fire detection.
   * `DHT11 / DHT22` Temperature Sensor for thermal spike detection.
3. **Actuators & Alarms:**
   * `Relay Modules` (Gas Valve control + Kitchen Power cutoff with Lighting isolation).
   * `Buzzer & Status LEDs` for local audio-visual alarms.
4. **Power Supply:** Regulated safe power unit.

### 💻 Software Stack
* **Embedded Firmware:** C++ (Developed via Arduino IDE).
* **IoT Cloud & Mobile UI:** Blynk Cloud Server & Blynk Mobile Application.
* **Web Presence:** HTML/CSS/JS Landing Page hosted on GitHub Pages.

---

## 🔄 4. System Lifecycle & Emergency Workflow (سيناريو التشغيل)

1. **Normal State (حالة الاستعداد):** The system monitors sensors continuously and streams normal telemetry to the Blynk dashboard.
2. **Detection State (رصد الخطر):** A sensor detects gas concentration, smoke, flame, or a sudden temperature spike exceeding safe thresholds and signals the `ESP32`.
3. **Automated Action State (الاستجابة الفورية الآلية):**
   * Triggers the local `Buzzer` and `LEDs`.
   * Cuts off kitchen power outlets via `Relay 1` while keeping primary lights ON.
   * Closes the main gas valve via `Relay 2`.
   * Dispatches an urgent Push Notification via Wi-Fi to the `Blynk App`.
4. **Resolution & Emergency Escalation (التحكم والحل):** The user reviews live status on the mobile app, can trigger a **One-Click Emergency Call** to the Fire Department, or perform a **Manual Override** once the environment is safe.

---

## 📐 5. Software Engineering Artifacts (مخرجات هندسة البرمجيات)

This repository is organized according to the **Software Development Life Cycle (SDLC)**:

```text
├── 01-Requirements/
│   ├── SRS_Document.pdf                 # Functional & Non-Functional Requirements
│   └── Risk_Analysis.md                 # Safety-critical hazard & mitigation matrix
├── 02-System-Design-UML/
│   ├── 1_Hardware_Software_Architecture.png
│   ├── 2_Use_Case_Diagram.png           # Actors, System Boundary, Include/Extend/Generalization
│   ├── 3_Use_Case_Descriptions.md       # Structured tables (UC-01 to UC-05)
│   ├── 4_State_Machine_Diagram.png      # Normal -> Detection -> Action -> Resolved
│   └── 5_Sequence_Diagram.png           # Real-time emergency interaction flow
├── 03-UI-and-Prototypes/
│   ├── Blynk_Mobile_UI_Screenshots/     # Mobile dashboard & emergency button views
│   └── Landing_Page_Preview.png         # Web interface preview
├── 04-Testing-and-QA/
│   └── Test_Cases_Report.md             # Input -> Run -> Observe -> Compare -> Fix
└── README.md
