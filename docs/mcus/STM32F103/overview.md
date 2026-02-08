# STM32F103 — Overview

## General Description

The **STM32F103** is an ARM Cortex-M3 microcontroller by **STMicroelectronics**. The "Blue Pill" development board uses this chip and is one of the most popular entry-level ARM MCUs.

## Key Specifications

| Parameter | Value |
|-----------|-------|
| Manufacturer | STMicroelectronics |
| Core | ARM Cortex-M3 @ 72 MHz |
| Flash | 64–128 KB (variant dependent) |
| SRAM | 20 KB |
| GPIO | Up to 51 (depending on package) |
| ADC | 2× 12-bit, 1 µs conversion time |
| Timers | 4× general-purpose, 2× basic, 1× advanced (PWM) |
| UART | 3× (USART1–3) |
| SPI | 2× |
| I2C | 2× |
| USB | USB 2.0 Full Speed (Device) |
| CAN | 1× CAN 2.0B |
| Supply Voltage | 2.0–3.6 V |
| Package | LQFP-48, LQFP-64, LQFP-100 |

## Why This Chip Matters

- Entry-level ARM Cortex-M — the architecture used in most modern embedded systems
- ARM ecosystem: same architecture family as STM32F4, STM32H7, NXP LPC, etc.
- CMSIS and HAL libraries — industry-standard programming model
- SWD/JTAG debugging — real hardware debugging unlike AVR (basic debugWIRE)

## Architectural Contrast

| Feature | STM32F103 | ATmega328P | ESP32 |
|---------|-----------|-----------|-------|
| Core | Cortex-M3 (32-bit ARM) | AVR (8-bit) | Xtensa LX6 (32-bit) |
| Clock | 72 MHz | 16 MHz | 240 MHz |
| Flash | 128 KB | 32 KB | 4 MB (ext) |
| RAM | 20 KB | 2 KB | 520 KB |
| Debug | SWD/JTAG | debugWIRE | JTAG |
| USB | Yes | No | No (OTG on S2/S3) |
| DMA | Yes (7 channels) | No | Yes (13 channels) |

> TODO: Add architecture, clock tree, register map, and HAL vs LL comparison
