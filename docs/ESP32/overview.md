# ESP32 (WROOM-32) — Overview

## General Description

The **ESP32** is a low-cost, low-power system-on-chip (SoC) manufactured by **Espressif Systems**. It features dual-core Xtensa LX6 processors, integrated WiFi (802.11 b/g/n) and Bluetooth (Classic + BLE 4.2), and a rich set of peripherals.

## Key Specifications

| Parameter | Value |
|-----------|-------|
| Manufacturer | Espressif Systems |
| Type | WiFi/Bluetooth SoC |
| Core | Dual Xtensa LX6 @ 240 MHz |
| SRAM | 520 KB |
| Flash | External (typically 4 MB via SPI) |
| ROM | 448 KB |
| WiFi | 802.11 b/g/n, 2.4 GHz |
| Bluetooth | Classic + BLE 4.2 |
| GPIO | 34 programmable |
| ADC | 2× 12-bit SAR ADC, 18 channels |
| DAC | 2× 8-bit |
| SPI | 4× (SPI0/1 for flash, SPI2/3 for general) |
| I2C | 2× |
| UART | 3× |
| I2S | 2× |
| PWM | 16 channels (LED PWM) + MCPWM |
| Supply Voltage | 2.3–3.6 V |
| Package | QFN-48 (6×6 mm) |

## Key Features

- Dual-core with independent clock control
- Ultra-low-power co-processor (ULP) for deep-sleep tasks
- Hardware cryptographic accelerators (AES, SHA, RSA, ECC)
- Secure boot and flash encryption
- Hall sensor and temperature sensor
- Touch sensor (10 capacitive touch pins)
- Ethernet MAC interface
- SD/SDIO/MMC host controller
- JTAG debugging interface

## ESP32 Variant Comparison

| Variant | Core | WiFi | BT | Flash | Key Difference |
|---------|------|------|----|-------|----------------|
| **ESP32** | Dual Xtensa LX6 | ✓ | Classic + BLE 4.2 | External | Original, most peripheral-rich |
| ESP32-S2 | Single Xtensa LX7 | ✓ | ✗ | External | No Bluetooth, USB-OTG |
| ESP32-S3 | Dual Xtensa LX7 | ✓ | BLE 5.0 | External | AI acceleration, USB-OTG |
| ESP32-C3 | Single RISC-V | ✓ | BLE 5.0 | External | RISC-V core, cost-optimised |
| ESP32-C6 | Single RISC-V | ✓ (WiFi 6) | BLE 5.0 | External | WiFi 6, 802.15.4 (Thread/Zigbee) |
| ESP32-H2 | Single RISC-V | ✗ | BLE 5.0 | External | 802.15.4 only (Thread/Zigbee) |

## Module: ESP32-WROOM-32

The WROOM-32 module packages the ESP32 SoC with:
- 4 MB SPI flash
- 40 MHz crystal
- PCB antenna
- RF matching network and shielding can
- 38-pin breakout

## Datasheet

- [ESP32 Technical Reference Manual](https://www.espressif.com/sites/default/files/documentation/esp32_technical_reference_manual_en.pdf)
- [ESP32 Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_en.pdf)
- [ESP-IDF Programming Guide](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/)
