# 🛡️ SentinelCore: Smart Network Fortress
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)](https://www.python.org/downloads/)[![GitHub Issues](https://img.shields.io/github/issues/AsHfIEXE/SentinelCore)](https://github.com/AsHfIEXE/SentinelCore/issues)[![GitHub Stars](https://img.shields.io/github/stars/AsHfIEXE/SentinelCore?style=social)](https://github.com/AsHfIEXE/SentinelCore)[![Code Coverage](https://img.shields.io/codecov/c/github/AsHfIEXE/SentinelCore)](https://codecov.io/gh/AsHfIEXE/SentinelCore)[![Hacktoberfest](https://img.shields.io/badge/Hacktoberfest-2025-orange)](https://hacktoberfest.com/)[![Documentation](https://readthedocs.org/projects/sentinelcore/badge/?version=latest)](https://sentinelcore.readthedocs.io/)[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-2.1-4baaaa.svg)](https://github.com/AsHfIEXE/SentinelCore/blob/main/CODE_OF_CONDUCT.md)

\
**Built with**: FastAPI, Raspberry Pi, ESP32, Docker, React, 

In a world besieged by 1.5 billion IoT attacks and 90% of breaches driven by phishing, **SentinelCore** emerges as the **world’s first Raspberry Pi-based, plug-and-play AI-powered cybersecurity fortress**. Crafted by a solo developer, this revolutionary platform transforms a $35 Raspberry Pi 4 and three ESP32 nodes into an **enterprise-grade defense suite**, delivering real-time threat detection, rogue device isolation, parental controls, honeypot DNS traps, and cutting-edge vulnerability scanning. Hosted entirely locally with secure global access via **Cloudflare Tunnel**, SentinelCore empowers homes, SMBs, NGOs, journalists, activists, and cybersecurity enthusiasts to reclaim their networks with unmatched **privacy**, **simplicity**, and **power**.

---

## 🌟 Project Vision

SentinelCore is a **privacy-first, distributed, and AI-enhanced cybersecurity platform** that redefines network security. By combining **enterprise-grade capabilities** with **consumer-friendly simplicity**, it delivers:

- **High privacy**: 100% local processing, no cloud dependency (except optional secure API syncs).
- **Ease of deployment**: Zero-configuration setup for ESP32 nodes and users.
- **Real-time defense**: Autonomous AI-driven anomaly detection and mitigation.
- **Affordable scalability**: DIY components under $100, scalable with additional nodes.
- **Global accessibility**: Securely access the local UI and API from anywhere via Cloudflare Tunnel.

Designed for **homes**, **SMBs**, **NGOs**, **journalists**, **activists**, and **enthusiasts**, SentinelCore is a fortress that sees the cyber war before it begins.

---

## 🚀 Use Cases

- **Secure Home/SMB Wi-Fi**: Neutralize rogue IoT devices, phishing, and malware with AI-driven precision.
- **Privacy for NGOs/Journalists/Activists**: Safeguard communications in hostile environments with local-first, offline-capable operation.
- **Cybersecurity Education**: Hands-on platform for teaching network defense, AI, and distributed systems.
- **Research and Development**: Experiment with custom threat detection plugins, ML models, and mesh networks.

---

## ✨ SentinelCore Breakthroughs

 1. **Distributed AI-Powered Detection**: ESP32 nodes stream Wi-Fi/BLE data to lightweight AI models (ONNX/Sklearn) on the Pi, detecting anomalies like port scans or DNS tunneling in real-time.
 2. **True Plug-and-Play Mesh**: ESP32 nodes auto-connect to the Pi’s `SentinelCore_Fortress` hotspot, requiring no manual setup.
 3. **Rogue Device Isolation**: Instantly disconnect rogue devices/APs via ESP32 deauthentication or iptables, with one-click control.
 4. **Honeypot DNS Traps**: Lures malware with fake DNS endpoints, logging attacker behavior for analysis.
 5. **Network Vulnerability Scanning**: Scans devices for open ports, weak credentials, and outdated firmware, rivaling enterprise tools.
 6. **Exploit Watchdog**: Matches device OS/firmware to NIST NVD CVEs, delivering actionable mitigation alerts.
 7. **ML Device Fingerprinting**: Identifies device types (e.g., phone, camera) using passive traffic analysis, enhancing network visibility.
 8. **Python Plugin System**: Empowers users to write custom threat detection scripts in a secure sandbox, fostering innovation.
 9. **Offline Attack Map**: Visualizes rogue Wi-Fi/BLE signals with heat levels and historical patterns, exposing hidden threats.
10. **Self-Healing Watchdog**: Automatically restarts crashed services, ensuring fortress resilience with detailed alerts.

---

## 🔍 Core Features & Technology Map

| Feature | Description | Tech Stack |
| --- | --- | --- |
| **Network Discovery** | Maps LAN/Wi-Fi devices with IP, MAC, and vendor info. | Scapy, nmap, FastAPI, ESP32 scans |
| **Packet Capture** | Captures metadata of network flows (e.g., DNS, HTTP headers). | tcpdump, pyshark |
| **AI Anomaly Detection** | Detects abnormal behavior (e.g., port scans, DNS tunneling) with ML. | ONNX Runtime, Sklearn, custom rules |
| **Threat Scoring** | Assigns risk scores (0-100) to devices based on activity and vulnerabilities. | FastAPI, custom algorithm |
| **Interactive Dashboard** | Live network map, threat logs, alerts, and graphs with modular toggles. | React, Bolt UI, D3.js, Tailwind CSS |
| **Device Deauthentication** | Disconnects rogue devices/APs via ESP32 or iptables. | MQTT, ESP32 deauth, iptables |
| **Honeypot DNS Trap** | Redirects suspicious DNS to fake servers, logging attacker behavior. | dnsmasq, FastAPI logger, SQLite |
| **Parental Controls** | Blocks IPs/domains and schedules internet access. | dnsmasq, iptables |
| **OTA Firmware Updates** | Pushes firmware updates to ESP32 nodes from the dashboard. | FastAPI, ESP32 OTA client |
| **Voice Alerts** | Announces threats via local text-to-speech (e.g., “Rogue device detected!”). | pyttsx3 |
| **Network Vulnerability Scanner** | Scans devices for open ports, weak credentials, and outdated firmware. | nmap, Nikto, vulners.nse, FastAPI |
| **Exploit Watchdog** | Matches device OS/firmware to NIST NVD CVEs with mitigation recommendations. | NVD JSON parser, SQLite |
| **ML Device Fingerprinting** | Identifies device types (e.g., phone, camera) using passive traffic analysis. | p0f, fingerprintx, Scapy, Sklearn |
| **Python Plugin System** | Allows custom threat detection scripts in a sandboxed Python environment. | Python sandbox, FastAPI plugin manager |
| **Offline Attack Map** | Visualizes rogue Wi-Fi/BLE signals with heat levels and historical patterns. | D3.js, React, ESP32 scan data |
| **Firewall Rule Builder** | UI-driven iptables rules (e.g., block device, restrict hours). | FastAPI, iptables wrapper |
| **Notification Bots** | Sends alerts via Telegram, Signal, or Discord for threats and CVEs. | Telegram/Signal/Discord APIs |
| **IoT Behavior Modeling** | Learns IoT device traffic patterns, flags anomalies (e.g., unusual domains). | Sklearn, ONNX, FastAPI |
| **Network Time Machine** | Stores packet snapshots for historical browsing and diff analysis. | tcpdump, pyshark, SQLite |
| **Self-Healing Watchdog** | Restarts crashed services (MQTT, API, UI) with alerts and stacktraces. | systemd, Docker restart policies |

---

## 🚀 System Architecture Overview

SentinelCore is a **distributed, modular, and privacy-first** platform orchestrated by a Raspberry Pi 4 and three ESP32 nodes, communicating via MQTT over a dedicated Wi-Fi hotspot. The React/Bolt Web UI and FastAPI backend are hosted **locally** on the Pi, exposed globally via a **Cloudflare Tunnel** for secure, worldwide access without cloud hosting. Below is the network topology:

```
+---------------------------------------+               +------------------+
|           Internet/Router             |               |  User Device     |
| (for Pi Internet/Cloudflare Tunnel)   |               | (Laptop/Phone)   |
+------------------+--------------------+               +------------------+
                   | Ethernet/Wi-Fi (to Router for Internet)           ^
                   |                                                   |
                   |       Cloudflare Tunnel (Secure Internet Access)  |
                   |        +------------------------------------------+
                   |        |           (Exposes Pi services to public domain)
                   v        v
+------------------+---------------------------------------------------+
|                          Raspberry Pi 4 B (Central Hub)              |
|     +------------------------------------------------------------+   |
|     |  - Wi-Fi Hotspot (SSID: SentinelCore_Fortress)             |   |
|     |  - Mosquitto MQTT Broker                                   |   |
|     |  - Dockerized Backend + AI Inference Module (FastAPI)      |   |
|     |  - Web Dashboard UI (React/Bolt - SERVED LOCALLY)          |   |
|     |  - OTA Firmware Server                                     |   |
|     |  - Cloudflare Tunnel Client                                |   |
|     +------------------------------------------------------------+   |
+-----------------------------------^----------------------------------+
                                    | MQTT over Wi-Fi (Bi-directional)
                                    |
+------------------+      +------------------+      +------------------+
| ESP32 #1 Wi-Fi   |      | ESP32 #2 Deauth  |      | ESP32 #3 BLE +   |
| Scanner Node     |      | Module           |      | Wi-Fi Scanner    |
+------------------+      +------------------+      +------------------+
         |                      |                          |
  Passive Wi-Fi Scan       Deauth Rogue Devices       BLE + Wi-Fi Scan
```

### 1. Raspberry Pi 4B - Central Command Node

- **Services**:
  - Mosquitto MQTT broker (port 1883).
  - FastAPI backend API (port 5000) for core processing, AI inference, and plugin management.
  - Web Dashboard UI (React/Bolt, served via Nginx/Caddy on port 8080).
  - OTA firmware server (port 8000) for ESP32 updates.
  - Cloudflare Tunnel Client to expose UI and API to the internet.
- **Containers**: Dockerized for modularity and easy deployment.
- **Storage**: SQLite (default) or PostgreSQL (optional) for logs, configs, and history.
- **Network**:
  - Runs isolated Wi-Fi hotspot (`SentinelCore_Fortress`) via `hostapd` and `dnsmasq`.
  - Persistent internet connection via Ethernet or Wi-Fi (e.g., `wlan1` with second adapter, or `wlan0` to router) for Cloudflare Tunnel and optional external APIs (e.g., NVD CVE sync, Google Safe Browsing).

### 2. ESP32 Fleet

- **Node #1 (Wi-Fi Scanner)**: Passively scans Wi-Fi channels, collecting AP/client metadata (SSID, MAC, signal strength).
- **Node #2 (Deauth Actuator)**: Sends 802.11 deauth packets to isolate rogue devices/APs.
- **Node #3 (BLE + Wi-Fi Scanner)**: Scans BLE devices and supplements Wi-Fi coverage.
- **Firmware**: Arduino/PlatformIO with MQTT client, OTA downloader, and fail-safe watchdogs.

### 3. MQTT Communication

- **Broker**: Mosquitto MQTT on Pi (port 1883).
- **Topics**:
  - `esp32/{device_id}/scan`: Wi-Fi/BLE scan results.
  - `esp32/{device_id}/commands`: Deauth, reboot, or OTA commands.
  - `pi/alerts`: Threat notifications.
  - `pi/ota/firmware`: Firmware update payloads.
- **Benefits**: Lightweight, real-time, and decouples nodes for scalability.

### 4. Web UI (React )

- **Features**: Interactive network map (D3.js), threat logs, device details, modular toggles, vulnerability reports, and firewall rule builder.
- **Hosting**: Locally on Pi via Nginx/Caddy (port 8080), compiled as a static React/Bolt build.
- **Global Access**: Exposed via Cloudflare Tunnel (e.g., `https://dashboard.yourdomain.com`).
- **API Integration**: UI calls FastAPI backend via Cloudflare Tunnel URL (e.g., `https://api.yourdomain.com`) or relative paths.
- **UX**: Real-time updates via Socket.IO/Axios, sci-fi aesthetic with animated gauges (e.g., “Network Fortress Score”).

### 5. Data Pipeline

- ESP32 nodes publish scan data to MQTT.
- FastAPI backend validates and stores data in SQLite.
- AI module analyzes streams for anomalies, updating threat scores.
- Alerts trigger voice notifications (pyttsx3) or bot messages (Telegram/Discord).
- Dashboard visualizes live data, historical logs, and attack maps.

---

## 🌐 Network Topology

### 1. Wi-Fi Hotspot Mode

- **SSID**: `SentinelCore_Fortress`.
- **Components**: `hostapd` for AP, `dnsmasq` for DHCP (assigns IPs to ESP32s and user devices).
- **Benefits**: Isolated, secure environment; zero configuration for users.

### 2. Internet Connectivity

- Pi connects to Internet/Router via **Ethernet** (preferred) or **Wi-Fi** (`wlan1` with second adapter, or `wlan0` if connected to router) to maintain Cloudflare Tunnel and access external APIs.
- **Cloudflare Tunnel**: Exposes local UI (port 8080) and API (port 5000) to the internet via a custom domain or free subdomain (e.g., `dashboard.yourdomain.com`, `api.yourdomain.com`).
- No router port forwarding required; tunnel ensures secure access.

### 3. ESP32 Auto-Provisioning

- Firmware pre-programmed to seek `SentinelCore_Fortress` SSID and auto-connect to MQTT.
- No captive portals, QR codes, or CLI required.

---

## 📊 Software Microservices (Docker)

| Container | Role | Port | Language/Stack |
| --- | --- | --- | --- |
| **Mosquitto** | MQTT messaging backbone | 1883 | C |
| **Backend API** | Core processing, plugin mgr | 5000 | Python (FastAPI) |
| **AI Detection** | ML-based anomaly detection | Internal | Python, ONNX, Sklearn |
| **OTA Server** | ESP32 firmware updates | 8000 | Python |
| **Web Dashboard** | UI frontend (React/Bolt) | 8080 | React, Bolt, Tailwind, D3.js |
| **SQLite DB** | Logs, configs, history | Internal | SQLite |
| **Self-Healing** | Monitors and restarts services | Internal | systemd, Docker policies |
| **Cloudflare Tunnel** | Exposes UI/API to internet | Internal | Cloudflare Tunnel Client |

---

## 🎓 ESP32 Firmware Architecture

- **Platform**: Arduino/PlatformIO.
- **Common Modules**:
  - MQTT client (PubSubClient/AsyncMQTT) for scan data and commands.
  - OTA downloader and flasher for firmware updates.
  - Wi-Fi/BLE scanner for metadata (MAC, SSID, signal strength).
  - Command listener (e.g., reboot, deauth).
  - Fail-safe watchdogs for auto-reboot on disconnect.
- **Node #2 (Deauth)**:
  - Accepts MAC/channel via MQTT.
  - Sends 802.11 deauth frames to block rogue devices/APs.

---

## 🚪 Hardware Deployment Plan

| Device | Placement |
| --- | --- |
| **Raspberry Pi 4** | Central, protected, ventilated zone |
| **ESP32 #1** | Near router or Wi-Fi dense area |
| **ESP32 #2** | Central for optimal deauth range |
| **ESP32 #3** | Near BLE-rich area (e.g., IoT zone) |

- **Power**: USB adapters or centralized powered hub.
- **Optional**: Pi touchscreen for kiosk mode or used phone for AR visualization.

---

## 🚀 Setup & Deployment Guide

Detailed instructions in SETUP_GUIDE.md. Overview:

1. **Prepare Pi**:
   - Flash 64-bit Raspberry Pi OS Lite.
   - Enable SSH, install Docker/Docker Compose.
   - Configure `hostapd` + `dnsmasq` for hotspot (`SentinelCore_Fortress`).
   - Ensure internet access via Ethernet or Wi-Fi for Cloudflare Tunnel.
2. **Deploy Containers**:
   - Clone repository: `git clone https://github.com/AsHfIEXE/SentinelCore`.
   - Build React/Bolt UI and serve via Nginx/Caddy.
   - Run: `docker-compose up -d`.
3. **Set Up Cloudflare Tunnel**:
   - Install Cloudflare Tunnel Client on Pi.
   - Configure tunnel to expose UI (port 8080) and API (port 5000) to a custom domain (e.g., `dashboard.yourdomain.com`, `api.yourdomain.com`).
4. **Flash ESP32s**:
   - Use PlatformIO or Arduino IDE.
   - Upload firmware for Wi-Fi/BLE scanning and MQTT connectivity.
5. **Access UI**:
   - Locally: Connect to `SentinelCore_Fortress` Wi-Fi and visit `http://192.168.4.1:8080`.
   - Globally: Visit `https://dashboard.yourdomain.com` via Cloudflare Tunnel.

---

## 🎨 User Experience Flow

1. **Startup**: Plug in Pi and ESP32s; hotspot, MQTT, and Cloudflare Tunnel auto-configure in under a minute.
2. **Dashboard**: Explore a sci-fi-inspired UI with a live D3.js network map, threat scores, and vulnerability reports (local or global access).
3. **Alerts**: AI detects anomalies (e.g., rogue device, CVE match), triggering voice alerts (pyttsx3), Telegram/Discord notifications, or neon-lit visual warnings.
4. **Control**: Isolate rogues, block IPs, build firewall rules, or toggle modules with intuitive clicks.
5. **Analysis**: Dive into historical logs, attack heatmaps, or IoT behavior graphs for deep insights.
6. **Update**: Seamlessly push OTA firmware updates to ESP32s from the dashboard.
7. **Maintenance**: Self-healing watchdog ensures uptime, with health status in UI footer.

---

## ✅ Benefits & Differentiators

| Feature | Benefit |
| --- | --- |
| **Plug & Play** | Zero-config setup; ESP32s auto-connect to Pi hotspot. |
| **Private & Local-First** | Entire stack on Pi, zero cloud leakage, ideal for NGOs/activists. |
| **Real-Time Defense** | AI-driven detection, auto-isolation, and instant alerts. |
| **Global Access** | Securely access UI and API worldwide via Cloudflare Tunnel. |
| **Modular & Extendable** | Toggle features, add nodes, or write Python plugins. |
| **OTA Updates** | Remote firmware maintenance for ESP32s. |
| **Educational** | Hands-on learning for cybersecurity, AI, and distributed systems. |
| **Cost-Effective** | Entire system under $100 (Pi 4, ESP32s). |
| **Enterprise-Grade** | Vulnerability scans, CVE tracking, and ML fingerprinting rival commercial tools. |
| **Resilient** | Self-healing services ensure fortress uptime. |

---

## 📝 Project Status & Roadmap

- **Current Status**: MVP core features under development (network discovery, AI detection, dashboard, deauth).
- **Planned Milestones** (5-7 Weeks, Solo Build):
  - **Week 1-2**: Wi-Fi/BLE scanning, FastAPI backend, Bolt UI skeleton, Cloudflare Tunnel setup.
  - **Week 3-4**: Parental controls, honeypot DNS, vulnerability scanner, CVE watchdog.
  - **Week 5-6**: ML fingerprinting, Python plugin system, attack map, bot alerts.
  - **Week 7**: Firewall builder, IoT modeling, time machine, self-healing, exhibition prep.
- **Future Ideas**:
  - Router API integration for advanced hardening.
  - Mobile app for AR visualization and quick actions.
  - Local AI model retraining for personalized threat detection.

---

## 👥 Contributing

SentinelCore welcomes contributions from the community! To contribute:

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/new-plugin`).
3. Submit pull requests with clear descriptions.
4. Report bugs or suggest enhancements via Issues.
5. Follow CONTRIBUTING.md for guidelines.

---

## 📄 License

This project is licensed under the **MIT License**—see LICENSE for details.

---

## 🧑‍💻 About the Developer

SentinelCore is designed, developed, and maintained by **Salehin Ashfi**.

*"A fortress doesn’t need a thousand guards. Just one architect who sees the war before it begins."*

---

## 🎥 Demo & Exhibition Preview

Steal the spotlight at cybersecurity competitions with a **3-minute live demo** that showcases SentinelCore’s **enterprise-grade power** and **privacy-first design**:

- **Setup**: Raspberry Pi 4 powers the `SentinelCore_Fortress` hotspot; three ESP32 nodes scan Wi-Fi/BLE and isolate rogues; Pi connects to router via Ethernet/Wi-Fi for Cloudflare Tunnel, enabling global access at `dashboard.yourdomain.com`.
- **Interactive Flow**:
  1. **Threat Detection**: Dashboard reveals a rogue ESP32 device and flags a CVE-matched firmware vulnerability, with a neon-lit “Network Fortress Score” dropping to alert judges.
  2. **Rogue Isolation**: Judges click to isolate the rogue via ESP32 deauth or block a phishing domain, restoring the score with a satisfying animation.
  3. **Honeypot Trap**: Honeypot logs a malware DNS attempt, visualized in a D3.js attack heatmap showing rogue signal patterns.
  4. **IoT Insights**: IoT behavior graph flags an anomalous smart bulb, shifting from green to red, prompting a Telegram alert.
  5. **User Control**: Judges toggle AI detection, build a firewall rule (e.g., “Block YouTube after 9 PM”), or browse time machine logs, showcasing modularity.
  6. **Global Access**: Switch to a remote laptop, accessing the same dashboard via `dashboard.yourdomain.com`, proving secure, worldwide reach.
- **Visuals**: Neon-lit 3D-printed Pi case, 10” tablet displaying Bolt UI, QR stickers linking to GitHub, and a glowing “Fortress Points” leaderboard for judge interactions.
- **Pitch**: “SentinelCore is the **first-ever privacy-first cybersecurity fortress**, built by one visionary to shield your Wi-Fi, family, and freedom with AI-driven, enterprise-grade defense—accessible globally from a $35 Pi, unyielding and unstoppable.”
- **Handouts**: Flyers with QR codes to repo and a mini-guide for NGOs/activists on secure setup.

---

## 📸 Screenshots (Planned) (Coming Soon)

- **Network Map**: D3.js graph with devices, IPs, and pulsing threat scores.
- **Attack Map**: Heatmap of rogue Wi-Fi/BLE signals with historical patterns.
- **Vulnerability Report**: Table with CVSS scores, mitigation tips, and export button.
- **IoT Behavior Graph**: Green/yellow/red trends for device traffic anomalies.
- **Plugin Manager**: UI for uploading and toggling Python plugins.

---

## 🔗 Resources (Coming Soon)

- SETUP_GUIDE.md:  (Coming Soon) Complete installation and Cloudflare Tunnel setup.
- CONTRIBUTING.md: Contribution guidelines.
- GitHub Issues: Report bugs or suggest features.
- \[Planned Demo Video\]: (Coming Soon) 1-minute showcase of live threat detection and global access.