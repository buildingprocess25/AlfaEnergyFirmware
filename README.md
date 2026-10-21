# AlfaEnergy Official Firmware Distribution

Distribusi resmi firmware binary untuk ekosistem pemantauan energi **AlfaEnergy**, dirancang khusus untuk perangkat IoT Smart Metering skala retail & enterprise dengan kustomisasi white-labeling penuh.

* Developed & Maintained by: **Dicky Rohid Fikra** ([@rohidfkra777](https://github.com/rohidfkra777))
* Organization: **[buildingprocess25](https://github.com/buildingprocess25)**
* Firmware Version: `16.0.0.1`

---

## 📦 Supported Hardware & Binaries

| Perangkat | Arsitektur / Chipset | File OTA (.bin) | File USB Flash (.factory.bin) | Deskripsi Hardware |
| :--- | :--- | :--- | :--- | :--- |
| **AlfaEnergy Plug** | RISC-V Architecture | [`AlfaEnergy_Plug.bin`](firmware/AlfaEnergy_Plug.bin) | [`AlfaEnergy_Plug.factory.bin`](firmware/AlfaEnergy_Plug.factory.bin) | Smart Plug AC Power Meter (Integrated Energy Metering, Relay GPIO4, Button GPIO9) |
| **AlfaEnergy CT** | Dual-Core 32-bit Architecture | [`AlfaEnergy_CT.bin`](firmware/AlfaEnergy_CT.bin) | [`AlfaEnergy_CT.factory.bin`](firmware/AlfaEnergy_CT.factory.bin) | Split-Core CT Clamp Energy Meter 100A (High-Accuracy CT Metering, LCD Driver, Button GPIO0) |

---

## 🌐 Official OTA Update URL (GitHub Pages)

Gunakan tautan langsung berikut pada kolom **OTA Url** di menu **Firmware Upgrade** Web UI perangkat:

* **AlfaEnergy Plug:**
  ```text
  https://buildingprocess25.github.io/AlfaEnergyFirmware/firmware/AlfaEnergy_Plug.bin
  ```

* **AlfaEnergy CT:**
  ```text
  https://buildingprocess25.github.io/AlfaEnergyFirmware/firmware/AlfaEnergy_CT.bin
  ```

*(Tautan di atas sudah otomatis terkonfigurasi secara default di dalam firmware perangkat).*

---

## 🔐 Checksum Integritas Keamanan (SHA-256)

Daftar hash kriptografis resmi untuk verifikasi integritas file sebelum flashing:

| File | Ukuran | SHA-256 Checksum |
| :--- | :--- | :--- |
| `AlfaEnergy_Plug.bin` | ~2.21 MB | `6B2829F8989FBD03C4278F9C971BC58E4D00D37DF2C3D86DD222A01412A49377` |
| `AlfaEnergy_Plug.factory.bin` | ~3.13 MB | `EBD92B07CF9D90E1D6D8C8930D4AF7D623C1046F0D63644DDECDAC3B53368901` |
| `AlfaEnergy_CT.bin` | ~2.21 MB | `E16CFECDCAAFEC865B790CE187B4CA83AC14DF16C1DE6F68FBB48C7DC888536F` |
| `AlfaEnergy_CT.factory.bin` | ~3.13 MB | `A5F189F4FF4EFB2EE6F44F9D9A6C458A6032396D8676BE2A8AC8F3BF050C1406` |

Daftar checksum lengkap juga tersedia di file [`firmware/SHA256SUMS.txt`](firmware/SHA256SUMS.txt).

---

## ⚡ Panduan Flashing

### 1. Flashing Awal via USB-to-Serial
Gunakan file biner `.factory.bin` dan flash mulai dari alamat offset `0x00000`:

* **Parameter Flashing:**
  - File: `AlfaEnergy_XX.factory.bin`
  - Address Offset: `0x00000`
  - SPI Speed: `40MHz`
  - SPI Mode: `DIO`

### 2. Update OTA (Over-The-Air)
* Buka Web UI perangkat -> Masuk ke menu **Firmware Upgrade**.
* **Opsi A (Online OTA):** Pastikan kolom **OTA Url** terisi URL resmi GitHub Pages di atas, lalu klik **Start upgrade**.
* **Opsi B (Local Upload):** Unggah file `.bin` biasa (`AlfaEnergy_Plug.bin` atau `AlfaEnergy_CT.bin`) melalui menu **Upgrade by file upload**.

---

## 🛠️ Fitur Sistem & Kontrol Perangkat

* **Branding:** Antarmuka Web UI custom penuh dengan skema warna enterprise.
* **Reset Wi-Fi Hotspot:** Tekan tombol fisik sebanyak **6 kali cepat** untuk memancarkan Access Point darurat `AlfaEnergy_XX-XXXXXX` (IP default: `192.168.4.1`).
* **Factory Reset:** Tahan tombol fisik selama **~40 detik** hingga lampu indikator berkedip cepat untuk menghapus memori NVS dan kembali ke setelan default.
* **MQTT Telemetri:**
  - Format FullTopic: `AlfaEnergy/%topic%/%prefix%/`
  - Topic Identitas: Menggunakan 6 digit terakhir MAC Address perangkat (`%06X`).

---

## 📄 License
This repository distributes pre-compiled firmware binaries licensed under the [GNU General Public License v3.0](LICENSE).  
AlfaEnergy branding, custom UI themes, device profiles, and system integrations are Copyright © Dicky Rohid Fikra.