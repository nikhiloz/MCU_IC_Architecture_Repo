# SI4735 — Firmware & Boot Process

## Boot Sequence

1. Power applied to VDD
2. Internal power-on reset (POR) initialises digital logic
3. Reference oscillator starts (32.768 kHz crystal)
4. Device waits for `POWER_UP` command from host MCU
5. On `POWER_UP`:
   - Internal PLLs lock to reference clock
   - DSP firmware loads from internal ROM
   - Selected band (FM/AM) initialised
   - CTS bit set in status — device ready

## Firmware Patching (SI4735-D60)

The SI4735-D60 supports loading firmware patches via I2C to add features not in ROM (e.g., SSB demodulation).

### Patch Loading Sequence

1. Send `POWER_UP` with patch enable bit set (ARG1 bit 4 = 1)
2. Wait for CTS
3. Send patch data in 8-byte chunks via I2C:
   ```
   [0x15] [data0] [data1] ... [data6]
   ```
   (Command 0x15 = undocumented patch upload command)
4. Repeat for all patch blocks (~2000 blocks for SSB patch)
5. After last block, device automatically applies patch
6. Wait for CTS — patched device ready

### SSB Patch

- Adds USB/LSB demodulation to AM/SW bands
- Approximately 15 KB of patch data
- Must be re-loaded on every power cycle
- BFO offset configurable via property after patch load

## Firmware Versions

- Read via `GET_REV` command (0x10)
- Returns: firmware major, minor, patch ID, component versions

> TODO: Document GET_REV response format and known firmware versions
