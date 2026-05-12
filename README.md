# Simple WiFi-Controlled Mobile Robot Car

A WiFi-controlled mobile robot car built on **NodeMCU (ESP8266)**, programmed using **Arduino IDE**. The robot receives movement commands via HTTP requests over a local WiFi network and supports 8-directional movement, speed control, a buzzer horn, and LED headlights. This was a university assignment for an Electronics System Design course.

---

## Features

- **8-Direction Movement** : Forward, Backward, Left, Right, and all 4 diagonal directions
- **Variable Speed Control** : 10 speed levels (0–9 + max) adjustable via HTTP command
- **Buzzer Horn** : triggered on command
- **LED Headlight** : toggle on/off remotely
- **Dual WiFi Mode** : connects to existing network (STA mode) or creates its own hotspot (AP mode) if connection fails
- **OTA Firmware Update** : update the firmware wirelessly via Arduino OTA
- **Auto Hostname** : generates a unique hostname based on the chip's MAC address

---

## Tech Stack

| Technology | Description |
|------------|-------------|
| C++ / Arduino | Firmware programming language |
| Arduino IDE | Development environment |
| NodeMCU (ESP8266) | WiFi-enabled microcontroller |
| ESP8266WiFi | WiFi connectivity library |
| ESP8266WebServer | HTTP server for receiving commands |
| ArduinoOTA | Over-the-air firmware update |
| Blynk | IoT platform (included in dependencies) |

---

## Hardware & Pin Mapping

| Pin | Component | Function |
|-----|-----------|----------|
| D1 (PWMA) | Motor A | Speed control (PWM) |
| D2 (PWMB) | Motor B | Speed control (PWM) |
| D3 (DA) | Motor A | Direction control |
| D4 (DB) | Motor B | Direction control |
| D5 | Buzzer | Horn output |
| D8 | LED | Headlight output |
| D0 | WiFi LED | WiFi status indicator |

---

## HTTP Command Reference

Control the robot by sending HTTP requests with a `State` parameter:

| Command | Action |
|---------|--------|
| `?State=F` | Move Forward |
| `?State=B` | Move Backward |
| `?State=R` | Turn Right |
| `?State=L` | Turn Left |
| `?State=G` | Forward Left |
| `?State=H` | Backward Left |
| `?State=I` | Forward Right |
| `?State=J` | Backward Right |
| `?State=S` | Stop |
| `?State=V` | Beep Horn |
| `?State=W` | LED On |
| `?State=w` | LED Off |
| `?State=0`–`9` | Set Speed Level |
| `?State=q` | Max Speed |

---

## File Structure

```
project-simple-mobile-robot-car/
└── pemrograman      # Main Arduino/C++ firmware file
```

---

## 🚀 Getting Started

### Prerequisites
- [Arduino IDE](https://www.arduino.cc/en/software) installed
- ESP8266 board package installed in Arduino IDE
- Required libraries: `ESP8266WiFi`, `ESP8266WebServer`, `ArduinoOTA`, `BlynkSimpleEsp8266`

### Setup & Upload

1. Clone this repository:
   ```bash
   git clone https://github.com/bellatrijuliana/project-simple-mobile-robot-car.git
   ```
2. Open `pemrograman` in Arduino IDE.
3. Update WiFi credentials in the code:
   ```cpp
   String sta_ssid = "YOUR_WIFI_NAME";
   String sta_password = "YOUR_WIFI_PASSWORD";
   ```
4. Select **NodeMCU 1.0 (ESP-12E Module)** as the board.
5. Upload the firmware to the NodeMCU.
6. Open Serial Monitor at **115200 baud** to see the assigned IP address.
7. Send HTTP commands to control the robot:
   ```
   http://<IP_ADDRESS>/?State=F
   ```

---

## What I Learned

- Programming an **ESP8266 microcontroller** with Arduino IDE
- Setting up an **HTTP web server** on an IoT device
- Implementing **PWM motor control** for differential drive
- Handling **dual WiFi modes** (STA and AP fallback)
- Enabling **OTA firmware updates** for wireless development
- Mapping HTTP commands to physical hardware actions

---

*Built as a university Electronics System Design course assignment.*
