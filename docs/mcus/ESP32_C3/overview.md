# ESP32-C3 — Overview

## General Description

The **ESP32-C3** is a single-core **RISC-V** based WiFi/BLE SoC by **Espressif Systems**. It provides a cost-optimised alternative to the original ESP32, with the notable difference of using a RISC-V core instead of Xtensa.

## Key Specifications

| Parameter | Value |
|-----------|-------|
| Manufacturer | Espressif Systems |
| Core | Single 32-bit RISC-V @ 160 MHz |
| SRAM | 400 KB |
| Flash | External (typically 4 MB via SPI) |
| ROM | 384 KB |
| WiFi | 802.11 b/g/n (2.4 GHz) |
| Bluetooth | BLE 5.0 |
| GPIO | 22 |
| ADC | 2× 12-bit SAR ADC, 6 channels |
| SPI | 3× |
| I2C | 1× |
| UART | 2× |
| Supply Voltage | 3.0–3.6 V |
| Package | QFN-32 (5×5 mm) |

## Architectural Contrast with ESP32 (Xtensa)

| Feature | ESP32-C3 (RISC-V) | ESP32 (Xtensa) |
|---------|-------------------|----------------|
| ISA | RISC-V (RV32IMC) | Xtensa LX6 |
| Cores | 1 | 2 |
| Clock | 160 MHz | 240 MHz |
| RAM | 400 KB | 520 KB |
| BT Classic | No | Yes |
| BLE Version | 5.0 | 4.2 |
| GPIO | 22 | 34 |
| Open ISA | Yes (RISC-V is open) | No (Xtensa is proprietary) |
| Cost | Lower | Higher |
| Secure Boot | V2 (RSA-3072) | V1/V2 |

## Why Study This Chip

- **RISC-V architecture**: Open-source ISA — you can study the instruction set fully
- Direct comparison with ESP32 Xtensa — same SDK (ESP-IDF), different CPU core
- Demonstrates how ISA choice affects: toolchain, code generation, performance

> TODO: Add RISC-V instruction set details, architecture comparison with Xtensa
