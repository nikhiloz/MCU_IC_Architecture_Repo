# CC1101 — Overview

## General Description

The **CC1101** is a low-cost sub-1 GHz RF transceiver by **Texas Instruments**. Operates in ISM bands (315/433/868/915 MHz) for wireless sensor networks, remote controls, and IoT.

## Key Specifications

| Parameter | Value |
|-----------|-------|
| Manufacturer | Texas Instruments |
| Type | Sub-GHz RF Transceiver |
| Frequency | 300–348 MHz, 387–464 MHz, 779–928 MHz |
| Modulation | 2-FSK, 4-FSK, GFSK, MSK, OOK, ASK |
| Data Rate | 1.2–500 kbps |
| Interface | SPI |
| Supply Voltage | 1.8–3.6 V |
| TX Power | -30 to +12 dBm (programmable) |
| RX Sensitivity | -116 dBm @ 0.6 kbps |
| Package | QLP-20 (4×4 mm) |

## Key Features

- Programmable packet engine (sync word, CRC, address filtering)
- Built-in FIFO buffers (64 bytes TX, 64 bytes RX)
- Wake-on-Radio (WOR) for low-power listening
- Digital RSSI output
- Clear Channel Assessment (CCA)

## Contrast with ESP32

| Feature | CC1101 | ESP32 |
|---------|--------|-------|
| Frequency | Sub-GHz | 2.4 GHz |
| Protocol | Custom / proprietary | WiFi, Bluetooth |
| Range | Long range (km with proper antenna) | Short-medium (tens of metres) |
| CPU | None (SPI peripheral) | Dual-core Xtensa |
| Use case | Simple sensor networks | Full IoT applications |

> TODO: Add SPI register map, packet format, and configuration examples

---

**← Prev** [R820T2](../R820T2/) · [↑ Back to Main README](../../../README.md) · **Next →** [ATmega328P](../../mcus/ATmega328P/)
