
# 🛠️ HDD-ToolBox Cyberpunk (Secure Edition)

> **HDD-ToolBox** is a highly specialized "Swiss Army Knife" for storage media. It combines professional Linux low-level utilities with a modern cyberpunk web interface and artificial intelligence.
This distribution is based on **Ubuntu 24.04 (Noble Numbat)** and is delivered as a hardened Docker image with an encrypted application core.

---
## 🚀 Key Advantages

* **Unified Interface:** No more juggling dozens of CLI tools; manage everything from one dashboard.
* **NOVA AI Integration:** Get expert guidance and automated analysis of S.M.A.R.T. data.
* **Multi-Platform:** Seamlessly switch between your desktop PC and your Raspberry Pi.
* **Safe Environment:** All tools are pre-configured inside a hardened Ubuntu 24.04 environment, preventing dependency hell on your host system.
* **Protected Core:** The application logic is encrypted (Pyarmor) to ensure stability and security.
---
## 🛠️ Developed With

This project leverages the best-in-class open-source and security technologies:

* **OS Base:** Ubuntu 24.04 LTS (Noble Numbat)
* **Language:** Python 3.12+ (Flask Backend)
* **Frontend:** HTML5, CSS3 (Cyberpunk UI Framework), JavaScript
* **AI Engine:** NOVA AI (via OpenRouter / OpenAI API)
* **Security:** Pyarmor (Core Encryption), SHC (Shell Script Compiler)
* **Tools:** smartmontools, hdparm, nvme-cli, fdisk, parted, udisks2

## 📋 Prerequisites & Security

### **Requirements**
* **OS:** Linux with Docker & Docker Compose installed.
* **Arch:** Supported for `AMD64` (PC) and `ARM64` (Raspberry Pi).
* **Mode:** The container **must** run in `privileged: true` mode for hardware access.

### **⚠️ Risk Disclosure**
* **Admin Privileges:** The frontend operates with high-level administrative permissions. This is required for disk manipulation.
* **Data Loss:** Incorrect use of formatting or partitioning tools can lead to **irreversible data loss**.
* **Access:** Use a strong password. Do not expose port `5000` to the public internet without a VPN or Reverse Proxy.
  
## ✨ Features at a Glance

### 🤖 NOVA AI Assistant
- **Intelligent Analysis:** NOVA evaluates terminal outputs and S.M.A.R.T. data in real-time to provide actionable recommendations.
- **Natural Language Control:** Issue complex commands in plain language; NOVA generates and explains the appropriate shell command for you.
- **Contextual Knowledge:** NOVA recognizes the condition of your drives and provides proactive warnings about potential risks.

### 🩺 Diagnostics & Monitoring
- **Deep S.M.A.R.T. Check:** Full attribute analysis for HDD, SSD, and NVMe drives.
- **Hardware Self-Tests:** Trigger Short and Long self-tests directly from the web interface.
- **Live Status:** Real-time display of temperature, power-on hours, and overall health status.

### 🧩 Partitioning & Formatting
- **Auto-Setup:** 1-Click partitioning for Linux (EXT4), Windows (NTFS), macOS (HFS+), or Universal (exFAT).
- **GPT/MBR Management:** Full support for modern and legacy partition tables via `parted` and `fdisk`.
- **Wipe Option:** Optional "Zero-Fill" (overwriting sectors) during the formatting process.

### 🔒 Data Security & Sanitization
- **ATA Secure Erase:** Hardware-based erasure for SATA drives (via `hdparm`).
- **NVMe Format:** Specialized low-level formatting for modern M.2/U.2 SSDs.
- **DoD Standard:** Secure wiping with multiple passes using `shred`.
- **SSD Blkdiscard:** Instant resetting of SSD cells via TRIM/Discard commands.

### 💾 Backup & Recovery
- **Image Cloning:** Create 1:1 raw images of your drives (.img).
- **Web Download:** Download your backups directly through your browser.
- **Restore:** Safely write local images back to physical drives.
- **File Restore:** Integrated support for recovering deleted files using `extundelete`.
---

📦 Deployment (Choose your Architecture)

### 🖥️ 1. AMD64 (PC / Server)
```YAML
services:
  hdd-toolbox:
    image: ghcr.io/jeromex/hdd-toolbox-amd64:latest
    container_name: hdd-toolbox
    privileged: true
    restart: always
    ports:
      - "5000:5000"
    volumes:
      - /dev:/dev
      - /run/udev:/run/udev:ro
      - ./data:/opt/tuxhausen/data
      - /media:/media:rshared
```
---------------------------------------------------------------------------------
### 🍓 2. ARM64 (Raspberry Pi)
```YAML
services:
  hdd-toolbox:
    image: ghcr.io/jeromex/hdd-toolbox-rpi:latest
    container_name: hdd-toolbox-rpi
    privileged: true
    restart: always
    ports:
      - "5000:5000"
    volumes:
      - /dev:/dev
      - /run/udev:/run/udev:ro
      - ./data:/opt/tuxhausen/data
      - /media:/media:rshared
```
<img width="1920" height="1080" alt="2026-04-16 19_02_25-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/91351288-f2d3-4bc5-9523-9d929d09a1cb" />
<img width="1920" height="1080" alt="2026-04-16 19_02_43-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/12a6bd26-cdff-4d64-9a3f-5a9adfd2914a" /><img width="1920" height="1080" alt="2026-04-16 19_02_59-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/6e78b034-3e0a-4578-8134-e15d158d2d89" /><img width="1920" height="1080" alt="2026-04-16 19_03_10-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/e9d8778b-364b-4b53-b5c1-0857ab20db77" />
<img width="1920" height="1080" alt="2026-04-16 19_03_23-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/0024025b-9972-4733-8aa1-e72da9e48ea6" />
<img width="1920" height="1080" alt="2026-04-16 19_03_36-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/d2655e66-873c-490e-aed9-ac1265a299d7" />
<img width="1920" height="1080" alt="2026-04-16 19_04_27-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/a05aa273-082d-4334-9932-aec6aa08f951" />
<img width="1920" height="1080" alt="2026-04-16 19_04_16-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/174ec83d-a265-4658-ab01-2bb154f29d0b" />
<img width="1920" height="1080" alt="2026-04-16 19_17_17-HDD-ToolBox (Cyberpunk Docker)" src="https://github.com/user-attachments/assets/a23d6ae7-5fa9-4358-9ddf-4d8aa09c2a70" />

### © 2026 Malte Speck - Professional Storage Solutions
