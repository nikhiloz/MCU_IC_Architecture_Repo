# R820T2 — Overview

## General Description

The **R820T2** is a wideband RF tuner IC by **Rafael Micro**. Commonly paired with the RTL2832U in SDR dongles, it converts RF signals (24 MHz–1.766 GHz) to an intermediate frequency for digitisation.

## Key Specifications

| Parameter | Value |
|-----------|-------|
| Manufacturer | Rafael Micro |
| Type | Wideband RF Tuner |
| Frequency Range | 24–1766 MHz |
| Interface | I2C (controlled by RTL2832U) |
| IF Output | 3.57 MHz (configurable) |
| Supply Voltage | 3.3 V |
| Package | QFN-24 |

## Role in SDR Dongle

```
┌──────────┐     ┌──────────┐     ┌──────────┐
│ Antenna  │────►│ R820T2   │────►│ RTL2832U │────► USB → PC
│          │     │ RF Tuner │     │ ADC/USB  │
│          │     │ LNA+Mix  │     │ 8-bit IQ │
└──────────┘     └──────────┘     └──────────┘
```

- **LNA**: Low noise amplifier (configurable gain)
- **Mixer**: Down-converts RF to IF
- **PLL**: Programmable local oscillator for frequency selection
- **IF filter**: Bandwidth selection

> TODO: Add register map, gain stages, and noise figure documentation

---

**← Prev** [RTL2832U](../RTL2832U/) · [↑ Back to Main README](../../../README.md) · **Next →** [CC1101](../CC1101/)
