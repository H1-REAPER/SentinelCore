# 🛡️ SentinelCore: Smart Network Fortress

![MIT License](https://img.shields.io/badge/license-MIT-blue)
![Built with FastAPI](https://img.shields.io/badge/Built%20with-FastAPI-005571?logo=fastapi)
![Raspberry Pi](https://img.shields.io/badge/hardware-Raspberry%20Pi-red)
![ESP32](https://img.shields.io/badge/device-ESP32-blue)

**The world’s first Raspberry Pi-based, plug-and-play AI-powered cybersecurity fortress** for homes, SMBs, NGOs, journalists, activists, and cybersecurity enthusiasts.





```
+------------------+                        +--------------------------+
|  User Device     | <----Wi-Fi---->       | Raspberry Pi 4 B         |
| (Laptop/Phone)   |                       | - Hotspot (SentinelCore) |
|                  |                       | - MQTT Broker            |
+------------------+                       | - Dockerized Backend     |
         ^                                 | - AI Inference Module    |
         |                                 | - Web Dashboard (UI)     |
         |                                 +--------------------------+
         |                                          ^
         |                                          |
         |                                    MQTT over Wi-Fi
         |                                          v
+------------------+  +------------------+  +------------------+
| ESP32 #1 Wi-Fi   |  | ESP32 #2 Deauth  |  | ESP32 #3 BLE +   |
| Scanner Node     |  | Module           |  | Wi-Fi Scanner    |
+------------------+  +------------------+  +------------------+
     |                      |                       |
 Passive Wi-Fi Scan   Deauth Rogue Devices   BLE + Wi-Fi Scan
```

---

## 🌟 Project Vision

**SentinelCore** is a self-contained, distributed, and AI-enhanced cybersecurity platform that transforms a Raspberry Pi and a few ESP32 boards into a professional-grade network monitoring and defense suite.

Built **entirely by a solo developer**, this system is engineered for:

- High privacy (no cloud dependency)
- Ease of deployment (zero config onboarding)
- Real-time defense (autonomous anomaly detection + mitigation)
- Affordable scalability (DIY-friendly components)

### 🚀 Use Cases:

- Secure home/SMB networks from IoT attacks
- Safeguard activist/journalist comms in hostile environments
- Educational tool for teaching network security and distributed systems
- Research platform for anomaly detection, mesh networks, and edge computing

---

## ✨ SentinelCore Breakthroughs

- **Distributed AI-Powered Detection:** ESP32 scanner nodes feed real-time data into local lightweight anomaly detection models (ONNX/Sklearn) running on the Pi.
- **True Plug-and-Play Mesh:** ESP32 nodes auto-connect to the Pi’s hotspot with no manual setup.
- **Rogue Device Isolation:** One-click deauthentication via ESP32 command or iptables blocking.
- **Honeypot DNS Traps:** Identifies malware traffic through fake DNS endpoints.
- **Voice & Visual Alerts:** Local TTS alerts + live dashboard notifications.
- **Full Local Processing:** No cloud, no leaks. All AI, database, and MQTT comms stay on the Pi.
- **OTA Update Mechanism:** Push firmware updates to ESP32s from Pi dashboard.
- **Modular Services:** Toggle any feature (e.g., parental control, AI, honeypot) in UI.

---

## 🔍 Core Features & Technology Map

| Feature               | Description                           | Tech Stack                          |
| --------------------- | ------------------------------------- | ----------------------------------- |
| Network Discovery     | Maps all devices on LAN & Wi-Fi       | Scapy, nmap, FastAPI, ESP32 scans   |
| Packet Capture        | Metadata capture of network flows     | tcpdump, pyshark                    |
| AI Detection          | Abnormal behavior detection           | ONNX Runtime, Sklearn, Custom Rules |
| Threat Scoring        | Assigns risk score (0-100) per device | FastAPI + custom algorithm          |
| Interactive Dashboard | Live device map, logs, alerts, graphs | React, Bolt UI, D3.js               |
| Deauthentication      | ESP32 disconnects rogue devices       | MQTT command -> ESP32 Deauth        |
| Honeypot DNS          | Detects malware traffic via DNS baits | dnsmasq, FastAPI logger             |
| Parental Controls     | Block IPs/domains, schedule access    | dnsmasq, iptables                   |
| OTA Server            | Updates ESP32 firmware over-the-air   | FastAPI, ESP32 OTA client           |
| Voice Alerts          | Speak alerts on Pi speaker            | pyttsx3                             |
| Modular UI            | Enable/disable services on demand     | Docker, FastAPI config endpoints    |
| MQTT Broker           | Message bus between nodes and Pi      | Mosquitto MQTT                      |

---

## 🚀 System Architecture Overview

### 1. Raspberry Pi 4B - Central Command Node

- **Services**: MQTT Broker, FastAPI backend, AI engine, OTA server, dashboard
- **Containers**: Dockerized for modular deployment
- **Storage**: SQLite (or PostgreSQL optional)
- **Network**: Runs isolated Wi-Fi network via `hostapd` + `dnsmasq`

### 2. ESP32 Fleet

- **Node #1**: Passive Wi-Fi scanner (channels, clients, APs)
- **Node #2**: Wi-Fi Deauth actuator
- **Node #3**: BLE + Wi-Fi scanner for overlap and coverage

### 3. MQTT Communication

- Topics like `esp32/device_id/scan`, `esp32/device_id/commands`, `pi/alerts`
- Lightweight, real-time pub/sub between sensors and backend

### 4. Web UI (React + Bolt)

- Interactive live graph of network map
- Toggle features, see alerts, view scan history
- Local-only served by Nginx or Caddy

---

## 🌐 Network Topology

### 1. Wi-Fi Hotspot Mode

- `hostapd` creates SSID: **SentinelCore\_Fortress**
- `dnsmasq` assigns DHCP to ESP32s and user devices
- Ensures total isolation from home router if needed

### 2. Optional LAN Mode

- If internet via Ethernet is needed, Pi bridges its internal interface
- User devices can connect via Pi’s hotspot or LAN

### 3. ESP32 Auto Provisioning

- Firmware is pre-programmed to seek Pi’s SSID and auto-MQTT-connect
- No need for captive portals, QR code provisioning, or CLI

---

## 📊 Software Microservices (Docker)

| Container     | Role                  | Port     | Language/Stack          |
| ------------- | --------------------- | -------- | ----------------------- |
| Mosquitto     | MQTT messaging        | 1883     | C                       |
| Backend API   | Core processing       | 5000     | Python (FastAPI)        |
| AI Detection  | Applies ML rules      | Internal | Python + ONNX           |
| OTA Server    | ESP32 firmware        | 8000     | Python                  |
| Web Dashboard | UI frontend           | 8080     | React + Bolt + Tailwind |
| SQLite DB     | Logs, config, history | internal | SQLite                  |

---

## 🎓 ESP32 Firmware Architecture

- **Platform**: Arduino/PlatformIO

- **Common Modules**:

  - MQTT client (PubSubClient/AsyncMQTT)
  - OTA downloader + flasher
  - Wi-Fi + BLE scanner
  - Command listener (reboot, deauth, etc)
  - Fail-safe watchdogs for auto-reboot

- **Node #2** (Deauth)

  - Accepts MAC/channel via MQTT
  - Sends 802.11 deauth frames

---

## 🚪 Hardware Deployment Plan

| Device       | Placement                             |
| ------------ | ------------------------------------- |
| Raspberry Pi | Central, protected, ventilated zone   |
| ESP32 #1     | Near router or Wi-Fi dense area       |
| ESP32 #2     | Central for best deauth range         |
| ESP32 #3     | Near BLE-rich area (e.g., IoT corner) |

**Power**: USB adapters or centralized powered hub

**Optional**: Raspberry Pi touchscreen for kiosk mode

---

## 🚀 Setup & Deployment Guide

Refer to `SETUP_GUIDE.md` for complete instructions. Overview:

1. **Prepare Pi**

   - Flash 64-bit Raspberry Pi OS Lite
   - Enable SSH, install Docker/Docker Compose
   - Set up `hostapd` + `dnsmasq` for AP mode

2. **Deploy Containers**

   - Clone project
   - `docker-compose up -d`

3. **Flash ESP32s**

   - Use PlatformIO or Arduino IDE
   - Upload Wi-Fi scan + MQTT connect logic

4. **Open UI**

   - Connect to `SentinelCore_Fortress`
   - Visit `http://192.168.4.1:8080`

---

## 🎨 UX Flow Summary

- **Startup**: Plug Pi + ESP32s, everything auto-connects
- **Dashboard**: Real-time map, device info, alerts
- **Alerts**: AI flags anomalies, triggers voice + visual warnings
- **Control**: Click isolate, block, or schedule access from UI
- **Update**: ESP32s updated via OTA with no physical access

---

## ✅ Benefits & Differentiators

| Feature              | Benefit                                      |
| -------------------- | -------------------------------------------- |
| Plug & Play          | No manual config for ESP32s                  |
| Private & Offline    | No cloud, zero data leakage                  |
| Real-Time Defense    | Live alerts, auto-isolation of threats       |
| Modular & Extendable | Add new ESP32 nodes anytime                  |
| OTA Updates          | Fully remote firmware maintenance            |
| Educational          | Perfect for STEM/cybersecurity learning labs |
| Cost-Effective       | Entire system under \$100                    |

---

## 📝 Project Status & Roadmap

Current Status: **MVP Core Features Under Development**

Planned Milestones:

-

---

## 👥 Contributing

Pull requests, bug reports, and enhancement suggestions welcome!

- Fork the repo
- Submit issues and ideas
- Follow `CONTRIBUTING.md`

---

## 📄 License

**MIT License** — see `LICENSE` file.

---

**SentinelCore** is designed, developed, and maintained by **Salehin Ashfi**.

> "A fortress doesn't need a thousand guards. Just one architect who sees the war before it begins."

---
