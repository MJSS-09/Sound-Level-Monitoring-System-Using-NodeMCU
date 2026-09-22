<div align="center">

# 🔊 Sound Level Monitor

**Real-Time Sound Level Monitoring & Alert System using NodeMCU (ESP8266)**

[![Platform](https://img.shields.io/badge/platform-ESP8266-blue?logo=espressif&logoColor=white)](https://www.espressif.com/)
[![Board](https://img.shields.io/badge/board-NodeMCU-orange)](https://www.nodemcu.com/)
[![IDE](https://img.shields.io/badge/IDE-Arduino-00979D?logo=arduino&logoColor=white)](https://www.arduino.cc/)
[![Status](https://img.shields.io/badge/status-working-brightgreen)]()

```
🎙  Sound Sensor   →   🧠  NodeMCU ESP8266   →   💡  LED Alert Output
```

</div>

---

## 📖 Overview

This project uses a **NodeMCU ESP8266** paired with an analog sound sensor module to continuously measure ambient sound intensity, convert it into an approximate decibel (dB) value, and trigger a visual LED alert whenever the sound level crosses a configurable threshold. Live readings stream to the Arduino IDE Serial Monitor in real time.

It's a compact, hands-on demonstration of core embedded systems concepts — analog signal acquisition, real-time signal processing, threshold-based decision logic, and digital output control — and a solid launchpad for a future Wi-Fi-connected IoT noise-monitoring node.


<sub>Assembled hardware — NodeMCU ESP8266 with sound sensor & LED, live serial output visible on screen</sub>
</div>

---

## ✨ Features

- 📈 Real-time ambient sound sampling using a 50 ms sliding window
- 🔢 Peak-to-peak amplitude → voltage → approximate decibel (dB) conversion
- 🎚️ Configurable dB threshold (default: **60 dB**)
- 💡 Instant visual LED alert when the threshold is exceeded
- 🖥️ Continuous serial logging of readings at 115200 baud

---

## 🧰 Hardware Required

| Component | Qty |
|---|:---:|
| 🧠 NodeMCU ESP8266 Dev Board | 1 |
| 🎙️ Analog Sound Sensor Module | 1 |
| 💡 LED (5 mm, any color) | 1 |
| 🔗 Jumper wires (M–M / M–F) | As required |
| 🔌 Micro-USB cable | 1 |

---

## 🔌 Wiring

| NodeMCU Pin | Connects To |
|:---:|---|
| `A0` (Analog In) | Sound sensor module's analog output (AO) |
| `D1` (Digital Out) | LED anode (+), through a current-limiting arrangement |
| `3V3` / `VU` | Sound sensor module VCC |
| `GND` | Sound sensor module GND and LED cathode |

---

## ⚙️ How It Works

```
1. Sense    →  Microphone captures ambient sound, outputs an amplified analog signal
2. Sample   →  NodeMCU reads A0 over a 50 ms window, tracking min/max ADC values
3. Convert  →  Peak-to-peak amplitude → voltage → approximate dB (logarithmic)
4. Compare  →  dB value checked against the configured threshold
5. Act      →  LED turns ON if threshold exceeded, reading printed to Serial Monitor
```

> **⚠️ Note:** Reported dB values are relative and empirically scaled — not laboratory-calibrated to dB(SPL). They're best used for consistent, repeatable threshold comparisons rather than as an absolute acoustic reference.

---

## 🚀 Getting Started

### Prerequisites

- [Arduino IDE](https://www.arduino.cc/en/software) with the ESP8266 board package installed
- NodeMCU ESP8266, sound sensor module, and LED wired as described [above](#-wiring)

### Upload Steps

1. Clone this repository
2. Open `SoundLevelMonitor.ino` in the Arduino IDE
3. Select **NodeMCU 1.0 (ESP-12E Module)** as the board, and the correct COM port
4. Click **Upload**
5. Open the Serial Monitor at **115200 baud** to view live readings

---


## 📊 Results

Tested live with the Arduino IDE Serial Monitor open:

| Test Condition | Approx. Sound Level | LED State |
|---|:---:|:---:|
| 🤫 Silent room, no activity | ~25 dB | ⚪ OFF |
| 🗣️ Normal speech near mic | ~40–50 dB | ⚪ OFF |
| 👏 Hand clap close to sensor | 63–68 dB | 🔴 ON |
| 📢 Loud shout / sharp sound | 70+ dB | 🔴 ON |

**Key observations:**
- Responds to sound changes within a single 50 ms window — near-instantaneous alerts
- Quiet-room readings stayed low and stable, confirming a correctly captured noise floor
- LED behaved reliably, switching on only when the threshold was genuinely exceeded

---

## 🎥 Demo

📹 See `Sound_Sensor_Prj_Video.mp4` in this repo, or the [full project report](Sound_Level_Monitoring_Project_Report.pdf) for a complete walkthrough and write-up.

---

## 🏠 Applications

- 🏫 Library, classroom, or office noise-level monitoring
- 👶 Baby-room or hospital ward loud-sound alerts
- 🏭 Industrial workspace noise / hearing-safety alerts
- 🏡 Foundational sensing node for a smart-home system
- ☁️ Entry point for a Wi-Fi-connected IoT noise-logging dashboard

---

## 🔮 Future Scope

- [ ] 📡 Wi-Fi connectivity to push readings to a cloud dashboard
- [ ] 🗄️ Historical data logging for trend analysis
- [ ] 📱 Push notifications / mobile app alerts
- [ ] 🎯 Calibration against a reference sound level meter
- [ ] 🚦 Multi-level alerts (moderate / severe) with different LED colors or a buzzer
- [ ] 🔗 Integration with broader smart-home automation

---

## 👤 Author

**M . Jayantha Siva Srinivas**
B.Tech | Electronics and Communication Engineering
ESSCI-Certified Embedded Fullstack & IoT Analyst , SRM University(AP)
