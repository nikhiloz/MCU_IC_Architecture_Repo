# SI4735 — DSP Details

## Overview

The SI4735 performs nearly all signal processing in the digital domain after the ADC. The DSP handles demodulation, filtering, stereo decoding, RDS extraction, and automatic gain/frequency control.

## DSP Functions

### 1. Channel Filter
- Programmable IF bandwidth
- FM: 60 kHz, 84 kHz, 110 kHz, or 150 kHz (selectable)
- AM: 1 kHz to 6 kHz (programmable via properties)
- SW: Similar to AM bandwidth options
- Narrower bandwidth → better selectivity, wider → better audio quality

### 2. Demodulation
- **FM**: Digital frequency discriminator
- **AM**: Digital envelope detection
- **SSB** (SI4735-D60 with patch): Sideband selection (USB/LSB), BFO control

### 3. Automatic Gain Control (AGC)
- Digital AGC adjusts gain based on signal strength
- Configurable attack/decay time constants
- Prevents overload on strong signals, boosts weak signals
- Properties: `AM_AGC_ATTACK_RATE`, `AM_AGC_RELEASE_RATE`, `FM_AGC_ATTACK_RATE`, etc.

### 4. Stereo Decoder (FM)
- Decodes FM stereo multiplex (MPX) signal
- 19 kHz pilot tone detection
- L+R (mono) and L-R (stereo difference) extraction
- Stereo blend: gradually transitions mono↔stereo based on signal quality
- Property: `FM_BLEND_STEREO_THRESHOLD`, `FM_BLEND_MONO_THRESHOLD`

### 5. RDS/RBDS Decoder (FM)
- Extracts RDS data from 57 kHz subcarrier
- Decodes: Programme Service (PS), Radio Text (RT), Programme Type (PTY), Clock Time (CT)
- Interrupt-driven: host MCU polled or interrupt-notified when RDS data ready
- Command: `FM_RDS_STATUS`

### 6. Automatic Frequency Control (AFC)
- Corrects small frequency offsets
- Tracks carrier drift over time and temperature
- Status readable via `FM_TUNE_STATUS` → `READFREQ`

### 7. Seek Algorithm
- Scans across band looking for valid stations
- Configurable thresholds: RSSI, SNR, frequency spacing
- Commands: `FM_SEEK_START`, `AM_SEEK_START`

## SSB Firmware Patch (SI4735-D60)

The SI4735-D60 can load an SSB demodulation patch at boot:
- Patch loaded via I2C (approximately 15 KB)
- Enables USB/LSB reception on AM/SW bands
- BFO (Beat Frequency Oscillator) offset programmable ±16 kHz
- Command: `SSB_MODE` (after patch load)

> TODO: Document patch loading sequence and SSB-specific registers

## Signal Quality Indicators

| Indicator | Description | Command |
|-----------|-------------|---------|
| RSSI | Received signal strength (dBµV) | `FM_RSQ_STATUS` / `AM_RSQ_STATUS` |
| SNR | Signal-to-noise ratio (dB) | Same |
| Multipath | FM multipath interference level | `FM_RSQ_STATUS` |
| FreqOff | Frequency offset from tuned (kHz) | `FM_RSQ_STATUS` |
| Valid | Valid channel indicator | Same |

## DSP Configuration Properties

> TODO: Add complete table of DSP-related properties with addresses, ranges, and defaults
