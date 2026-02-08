# SI4735 — Power Management

## Supply Requirements

| Parameter | Min | Typ | Max | Unit |
|-----------|-----|-----|-----|------|
| VDD | 2.7 | 3.3 | 5.5 | V |
| Decoupling | — | 100 | — | nF |

## Power Consumption

| Mode | Current (typ) | Notes |
|------|--------------|-------|
| FM Receive | 17 mA | Normal operation |
| AM Receive | 15 mA | Normal operation |
| SW Receive | 15 mA | Normal operation |
| Power Down | 5 µA | After POWER_DOWN command |

## Power Modes

### Active Mode
- Full receive, DSP processing, audio output active
- Entered via `POWER_UP` command

### Power Down
- Ultra-low power standby
- Entered via `POWER_DOWN` command (0x11)
- All internal oscillators stopped
- I2C/SPI interface remains responsive for wake-up
- Wake via new `POWER_UP` command

## Power Sequencing

1. Apply VDD (2.7–5.5 V)
2. Wait for supply to stabilise (>10 ms recommended)
3. Pull RST high (if using reset pin) or send POWER_UP command
4. Send `POWER_UP` command with desired mode (FM/AM)
5. Wait for CTS (Clear To Send) bit in status byte
6. Device is ready for tuning

## Low-Power Tips

- Use `POWER_DOWN` when radio not in use
- In FM mode, reduce audio volume (`RX_VOLUME` property) to lower DAC current
- Use interrupt (GPO2/INT) instead of polling to reduce MCU activity
- Select narrower IF bandwidth when possible (reduces DSP load marginally)

> TODO: Add measured power consumption graphs
