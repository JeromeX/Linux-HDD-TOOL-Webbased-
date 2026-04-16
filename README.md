# 🛠️ TUXHAUSEN HDD-ToolBox (Secure Edition)

> **TUXHAUSEN HDD-ToolBox** is a highly specialized "Swiss Army Knife" for storage media. It combines professional Linux low-level utilities with a modern cyberpunk web interface and artificial intelligence.

This distribution is based on **Ubuntu 24.04 (Noble Numbat)** and is delivered as a hardened Docker image with an encrypted application core.
<img width="1920" height="1080" alt="2026-04-16 19_17_17-HDD-ToolBox (Cyberpunk Docker)" src="https://github.com/user-attachments/assets/a23d6ae7-5fa9-4358-9ddf-4d8aa09c2a70" />

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

