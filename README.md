# AlfaEnergy Official Firmware Distribution

Distribusi resmi firmware binary untuk ekosistem pemantauan energi **AlfaEnergy**, dirancang khusus untuk perangkat IoT Smart Metering retail & komersial dengan kustomisasi white-labeling dan skema warna korporat.

* Developed & Maintained by: **Dicky Rohid Fikra** ([@rohidfkra777](https://github.com/rohidfkra777))
* Organization: **[buildingprocess25](https://github.com/buildingprocess25)**
* Firmware Version: `16.0.0.1`

---

## 📦 Supported Hardware & Binaries

| Perangkat | Chipset / Arsitektur | File OTA (.bin) | File USB Flash (.factory.bin) | Deskripsi Hardware |
| :--- | :--- | :--- | :--- | :--- |
| **AlfaEnergy Plug** | ESP32-C3 (RISC-V) | [`AlfaEnergy_Plug.bin`](firmware/AlfaEnergy_Plug.bin) | [`AlfaEnergy_Plug.factory.bin`](firmware/AlfaEnergy_Plug.factory.bin) | Sonoff S60TPF Smart Plug (CSE7766 Metering, Relay GPIO4, Button GPIO9) |
| **AlfaEnergy CT** | ESP32-D0WD-V3 (Xtensa Dual-Core) | [`AlfaEnergy_CT.bin`](firmware/AlfaEnergy_CT.bin) | [`AlfaEnergy_CT.factory.bin`](firmware/AlfaEnergy_CT.factory.bin) | Sonoff POWCT 100A Clamp Meter (CSE7761 CT, TM1621 Display, Button GPIO0) |

---

## 🌐 Official OTA Update URL (GitHub Pages)

Gunakan tautan langsung berikut pada kolom **OTA Url** di menu **Firmware Upgrade** Web UI perangkat:

* **AlfaEnergy Plug (Smart Plug S60TPF):**
  ```text
  https://buildingprocess25.github.io/AlfaEnergyFirmware/firmware/AlfaEnergy_Plug.bin
  ```

* **AlfaEnergy CT (Clamp Meter POWCT):**
  ```text
  https://buildingprocess25.github.io/AlfaEnergyFirmware/firmware/AlfaEnergy_CT.bin
  ```

*(URL di atas sudah otomatis ter-pre-baked di dalam firmware sehingga Anda cukup mengklik **Start upgrade** pada Web UI).*

---

## 🔐 Checksum Integritas Keamanan (SHA-256)

Pastikan integritas file biner sebelum melakukan flashing serial USB:

| File | Ukuran | SHA-256 Checksum |
| :--- | :--- | :--- |
| `AlfaEnergy_Plug.bin` | ~2.21 MB | `6B2829F8989FBD03C4278F9C971BC58E4D00D37DF2C3D86DD222A01412A49377` |
| `AlfaEnergy_Plug.factory.bin` | ~3.13 MB | `EBD92B07CF9D90E1D6D8C8930D4AF7D623C1046F0D63644DDECDAC3B53368901` |
| `AlfaEnergy_CT.bin` | ~2.21 MB | `E16CFECDCAAFEC865B790CE187B4CA83AC14DF16C1DE6F68FBB48C7DC888536F` |
| `AlfaEnergy_CT.factory.bin` | ~3.13 MB | `A5F189F4FF4EFB2EE6F44F9D9A6C458A6032396D8676BE2A8AC8F3BF050C1406` |

Daftar checksum lengkap juga tersedia di [`firmware/SHA256SUMS.txt`](firmware/SHA256SUMS.txt).

---

## ⚡ Panduan Flashing

### 1. Flashing Awal via Kabel USB-to-Serial
Gunakan file `.factory.bin` dan flash mulai dari offset `0x00000`:

* **Menggunakan esptool.py:**
  ```bash
  # Erase flash lama (opsional, disarankan jika pertama kali)
  esptool.py --port COM_PORT erase_flash

  # Flash firmware factory
  esptool.py --port COM_PORT write_flash 0x00000 AlfaEnergy_Plug.factory.bin
  # ATAU
  esptool.py --port COM_PORT write_flash 0x00000 AlfaEnergy_CT.factory.bin
  ```

* **Menggunakan ESP Flash Download Tool / Web Flasher:**
  - File: `AlfaEnergy_XX.factory.bin`
  - Address: `0x00000`
  - SPI Speed: `40MHz`
  - SPI Mode: `DIO`

### 2. Update OTA (Over-The-Air)
* Masuk ke Web UI perangkat -> **Firmware Upgrade**.
* **Cara 1 (Online):** Pastikan kolom **OTA Url** terisi URL GitHub Pages di atas, lalu klik **Start upgrade**.
* **Cara 2 (File Upload):** Unggah file `.bin` biasa (`AlfaEnergy_Plug.bin` atau `AlfaEnergy_CT.bin`) melalui form **Upgrade by file upload**.

---

## 🛠️ Fitur & Pengaturan Khusus

* **Branding:** Full white-labeled Web UI dengan tema warna korporat Alfamart (Dark Navy, Golden Yellow, Alfamart Blue & Red).
* **Reset Wi-Fi Hotspot:** Tekan tombol fisik sebanyak **6 kali cepat** untuk memancarkan hotspot darurat `AlfaEnergy_XX-XXXXXX` (IP default: `192.168.4.1`).
* **Factory Reset:** Tahan tombol fisik selama **~40 detik** hingga LED berkedip cepat untuk menghapus konfigurasi dan mengembalikan ke setelan awal.
* **MQTT:**
  - Format FullTopic: `AlfaEnergy/%topic%/%prefix%/`
  - Client ID & Topic: Menggunakan 6 digit terakhir MAC Address perangkat (`%06X`).

---

## 📄 License
This repository distributes pre-compiled firmware binaries built on top of [Tasmota](https://github.com/arendst/Tasmota), licensed under the [GNU General Public License v3.0](LICENSE).  
AlfaEnergy branding, custom UI themes, device templates, and configuration profiles are Copyright © Dicky Rohid Fikra.