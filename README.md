# 🛠️ TUXHAUSEN HDD-ToolBox (Secure Edition)

> **TUXHAUSEN HDD-ToolBox** is a highly specialized "Swiss Army Knife" for storage media. It combines professional Linux low-level utilities with a modern cyberpunk web interface and artificial intelligence.

This distribution is based on **Ubuntu 24.04 (Noble Numbat)** and is delivered as a hardened Docker image with an encrypted application core.

---

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

## 🚀 Installation

### 1. For PC / Server (AMD64)
**File:** `docker-compose.yml`
```yaml
services:
  hdd-toolbox:
    image: ghcr.io/jeromex/hdd-toolbox-amd64:latest
    container_name: hdd-toolbox
    hostname: hdd-tool-station
    privileged: true
    restart: always
    ports:
      - "5000:5000"
    volumes:
      - /dev:/dev
      - /run/udev:/run/udev:ro
      - ./data:/opt/tuxhausen/data
      - /mnt:/mnt:rshared
      - /media:/media:rshared
----------------------------------------------------------------------------------------
### 2. For Raspberry Pi (ARM64 / RPI)
**File:** `docker-compose.yml`
```yaml
services:
  hdd-toolbox:
    image: ghcr.io/jeromex/hdd-toolbox-rpi:latest
    container_name: hdd-toolbox-rpi
    hostname: hdd-tool-pi
    privileged: true
    restart: always
    ports:
      - "5000:5000"
    volumes:
      - /dev:/dev
      - /run/udev:/run/udev:ro
      - ./data:/opt/tuxhausen/data
      # Required for accessing external USB drives on Raspberry Pi OS
      - /media:/media:rshared
      - /mnt:/mnt:rshared

<img width="1920" height="1080" alt="2026-04-16 19_02_25-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/f0618929-ba83-4f52-8e24-d694d7c4a58c" />
<img width="1920" height="1080" alt="2026-04-16 19_02_43-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/a1a037b1-e7f6-412d-805c-595359878af5" />
<img width="1920" height="1080" alt="2026-04-16 19_02_59-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/ba40cc48-5282-493e-9849-d975bb0f5303" />
<img width="1920" height="1080" alt="2026-04-16 19_03_10-HDD-ToolBox (Cyberpunk Docker) und 3weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/36eee620-2e52-44eb-a3ea-5b38424b5128" />
<img width="1920" height="1080" alt="2026-04-16 19_03_23-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/7b581928-f73e-4da1-b0a2-739b6600e469" />
<img width="1920" height="1080" alt="2026-04-16 19_03_36-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/d860af38-bbc3-48c9-8595-f3146a1b7253" />
<img width="1920" height="1080" alt="2026-04-16 19_03_58-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/7b47675e-04a3-46ea-8979-363062637720" />
<img width="1920" height="1080" alt="2026-04-16 19_04_03-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/1131f7ee-7da1-4c0d-85db-29db88df5736" />
<img width="1920" height="1080" alt="2026-04-16 19_04_16-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/91abf1f1-a720-4889-9eec-d889f180b6e9" />
<img width="1920" height="1080" alt="2026-04-16 19_04_27-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/ad0d21ae-3939-4197-b486-9a609a8a40b2" />
<img width="1920" height="1080" alt="2026-04-16 19_04_32-HDD-ToolBox (Cyberpunk Docker) und 3 weitere Seiten - Persönlich – Microsoft​ Ed" src="https://github.com/user-attachments/assets/7ca7e875-4a88-46e5-baf7-695456c5f0da" />
