# Patient Health Monitoring System using IoT (ESP32 + Blynk)

This project is an IoT-based **Patient Health Monitoring System** built using an **ESP32** microcontroller and multiple sensors. It continuously monitors:

- ✅ Body temperature (DS18B20)
- ✅ Room temperature & humidity (DHT11)
- ✅ Heart rate in BPM (HW-827 pulse sensor)

All collected data is sent to the **Blynk IoT Cloud** and can be monitored in real time via **mobile app** or **web dashboard**.

> This project was originally built as a mini-project for a 7th semester course, but is structured here as a reusable and extendable open-source project.

---

## ✨ Features

- Real-time monitoring of:
  - Body temperature (°C and °F)
  - Room temperature
  - Humidity (%)
  - Heart rate (BPM)
- ESP32-based, Wi-Fi enabled, fully wireless.
- Blynk IoT integration (mobile + web dashboard).
- Error handling for disconnected temperature sensor.
- Future-ready: can be extended with AI/ML for health prediction.

---

## 🧱 Hardware Used

- **ESP32-WROOM-32 Dev Module**
- **DS18B20** digital temperature sensor (for body temp)
- **DHT11** sensor (room temperature + humidity)
- **HW-827** analog pulse sensor (heart rate)
- 4.7 kΩ resistor (for DS18B20 pull-up)
- Breadboard, jumper wires, USB cable
- (Optional) Arduino Uno used during development for power/USB-serial

---

## 🔌 Wiring Overview

**DS18B20 (Body Temperature)**  
- VDD → 3.3V (ESP32)  
- GND → GND  
- DATA → GPIO 15  
- 4.7 kΩ resistor between DATA and 3.3V

**DHT11 (Room Temp & Humidity)**  
- VCC → 3.3V  
- GND → GND  
- DATA → GPIO 4

**HW-827 Pulse Sensor (Heart Rate)**  
- VCC → 3.3V  
- GND → GND  
- SIGNAL → GPIO 35 (ADC pin)

> ⚠️ Important: The ESP32 uses **3.3V logic**. Do NOT power the HW-827 pulse sensor from 5V when its signal output is connected directly to the ESP32 ADC.

---

## 🧰 Software & Libraries

- **Arduino IDE 2.x**
- **Blynk IoT** account & app
- Libraries used:
  - `Blynk` (BlynkSimpleEsp32)
  - `OneWire`
  - `DallasTemperature`
  - `DHT sensor library`
  - `PulseSensor Playground`

Install them from **Sketch → Include Library → Manage Libraries**.

---

## 📡 Blynk Setup

1. Create a new **Template** in Blynk (e.g., `Patient Health Monitor System`).
2. Note the:
   - `BLYNK_TEMPLATE_ID`
   - `BLYNK_TEMPLATE_NAME`
3. Create a **Device** from that template and copy its **Device Auth Token**.
4. Configure Virtual Pins (Datastreams):

| Datastream | Type    | Unit | Description          |
|-----------|---------|------|----------------------|
| V1        | Double  | °C   | Body temp (°C)       |
| V2        | Double  | °F   | Body temp (°F)       |
| V3        | Double  | °C   | Room temp            |
| V4        | Double  | %    | Humidity             |
| V5        | Integer | BPM  | Heart rate (BPM)     |

5. Design the dashboard with **Value Display** / **Gauge** widgets bound to V1–V5.

---
