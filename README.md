# ESP32-S3-IOT-Board-
Custom ESP32-S3 IoT development board with USB-C,  LiPo charging &amp; 3.3V regulation — designed from  scratch in EasyEDA
# ESP32-S3 IoT Development Board 🔌

A custom ESP32-S3-WROOM-1 IoT development board designed from scratch using EasyEDA. Features USB-C power input, LiPo battery charging, 3.3V regulation, and all supporting circuitry — fully routed with 100% completion.

> Designed by **Nallavelli Yuvraj** | ECE | [GitHub](https://github.com/yuvi1303) | [LinkedIn](https://www.linkedin.com/in/nallavelliyuvraj)

---

## 📐 Schematic

![Schematic](images/schematic.jpg)

---

## 📋 Bill of Materials

![BOM](images/schematic_BOM.jpg)

---

## 🖥️ PCB Layout

![PCB Layout](images/pcb_layout.jpg)

---

## 🟦 Gerber Preview

![Gerber Preview](images/Gerber_preview.jpg)

---

## 🧊 3D View — Top

![3D Top View](images/3D_top%20view.jpg)

---

## 🧊 3D View — Isometric

![3D Isometric View](images/3D_isolated%20view.jpg)

---

## ✨ Features

- **MCU** — ESP32-S3-WROOM-1 with WiFi + Bluetooth 5.0
- **Power input** — USB-C (TYPE-C-31-M-12) with CC1/CC2 resistors for proper USB-C power negotiation
- **Battery charging** — TP4056 LiPo charger IC with 1A charge current set via PROG resistor
- **Voltage regulation** — AMS1117-3.3 LDO regulator (5V → 3.3V)
- **Battery connector** — JST B2B-PH-K-S 2-pin LiPo connector
- **Decoupling network** — Multiple 10µF and 100nF capacitors on all power rails
- **Boot/Reset buttons** — Dedicated BOOT and RST tactile switches with 10K pullup resistors
- **Power LED** — Status indicator with 330Ω current limiting resistor
- **Routing** — 100% auto-routed (76/76 connections, 0 failures, 4 vias)
- **GND pour** — Full bottom layer copper fill for clean ground plane

---

## 📐 Board Specifications

| Parameter | Value |
|-----------|-------|
| Board dimensions | 60mm × 52.61mm |
| Layers | 2 (Top signal + Bottom GND pour) |
| Routing | 100% (76/76 connections) |
| Failed connections | 0 |
| Vias | 4 |
| PCB color | Blue |
| Surface finish | HASL Gold |
| Manufacturer | JLCPCB |
| Price (5 pcs) | $5.00 |
| Build time | 1–2 days |

---

## 🧰 Bill of Materials (BOM)

| Ref | Component | Value | Package | Qty |
|-----|-----------|-------|---------|-----|
| U1 | ESP32-S3-WROOM-1 | WiFi + BT MCU | SMD Module | 1 |
| U2 | AMS1117-3.3 | 3.3V LDO Regulator | SOT-223 | 1 |
| U3 | TP4056 | LiPo Charger IC | SOP-8 | 1 |
| USBC1 | TYPE-C-31-M-12 | USB-C Connector | SMD | 1 |
| CN1 | B2B-PH-K-S | JST 2-pin Battery Connector | TH | 1 |
| R1, R2 | Resistor | 10KΩ | 0402 | 2 |
| R3 | Resistor | 330Ω | 0402 | 1 |
| R4, R5 | Resistor | 5.1KΩ | 0402 | 2 |
| R6 | Resistor | 1.2KΩ | 0402 | 1 |
| C1, C6, C7 | Capacitor | 10µF | 0805 | 3 |
| C2, C3, C4 | Capacitor | 100nF | 0402 | 3 |
| C5 | Capacitor | 10µF | 0805 | 1 |
| SW1 | Tactile Switch | RST Button | TS24CA | 1 |
| SW2 | Tactile Switch | BOOT Button | TS24CA | 1 |
| LED1 | LED | Power Indicator | 0402 | 1 |

---

## 🔌 Circuit Overview

```
USB-C (5V VBUS)
    │
    ├──► CC1, CC2 ──► 5.1KΩ ──► GND   (USB-C power negotiation)
    │
    ├──► TP4056 VCC (LiPo Charger)
    │         ├── PROG ──► 1.2KΩ ──► GND  (sets 1A charge current)
    │         ├── EP   ──► GND
    │         └── BAT  ──► JST Battery Connector (+)
    │
    └──► AMS1117-3.3 VIN
              └── VOUT (3.3V)
                    │
                    ├──► ESP32-S3-WROOM-1 3V3 pin
                    │         ├── EN  ──► R1 10K ──► 3V3
                    │         │         └── SW1 RST  ──► GND
                    │         ├── IO0 ──► R2 10K ──► 3V3
                    │         │         └── SW2 BOOT ──► GND
                    │         └── IO2 ──► R3 330Ω ──► LED ──► GND
                    │
                    └──► Decoupling caps (10µF + 100nF) ──► GND
```

---

## 💡 Key ECE Concepts Applied

| Concept | Where used |
|---------|-----------|
| USB-C CC resistors | 5.1KΩ on CC1 and CC2 for 5V power negotiation |
| LiPo charge current | PROG resistor 1.2KΩ sets charge current to 1A |
| Pullup resistors | 10KΩ on EN and IO0 for stable ESP32 boot behavior |
| Decoupling capacitors | 100nF + 10µF on every power rail near IC pins |
| Ground plane | Full copper pour on bottom layer reduces noise |
| Voltage regulation | AMS1117 LDO drops 5V USB input to clean 3.3V |

---

## 🗂️ Repository Structure

```
ESP32-S3-IoT-Board/
├── images/
│   ├── schematic.jpg
│   ├── schematic_BOM.jpg
│   ├── pcb_layout.jpg
│   ├── Gerber_preview.jpg
│   ├── 3D_top view.jpg
│   └── 3D_isolated view.jpg
├── gerber/
│   └── ESP32-S3-IoT-Board_Gerber.zip
└── README.md
```

---

## 🚀 How to Order This PCB

1. Download the `gerber/` folder ZIP file
2. Go to [JLCPCB.com](https://jlcpcb.com)
3. Click **Order Now → Upload Gerber**
4. Select: Qty **5**, Color **Blue**, Surface finish **HASL**
5. Order for ~$5 + shipping

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| EasyEDA Standard | Schematic design and PCB layout |
| LCSC Library | Component symbols and footprints |
| EasyEDA Auto-router | PCB trace routing (76/76 — 100%) |
| JLCPCB | PCB manufacturing and Gerber preview |

---

## 👤 Author

**Nallavelli Yuvraj**
Electronics & Communication Engineering (ECE)
Passionate about Embedded Systems, PCB Design and IoT

[![GitHub](https://img.shields.io/badge/GitHub-yuvi1303-black?logo=github)](https://github.com/yuvi1303)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-nallavelliyuvraj-blue?logo=linkedin)](https://www.linkedin.com/in/nallavelliyuvraj)

---

*If you find this project useful, please ⭐ star the repository!*
