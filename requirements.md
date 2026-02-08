# Requirements — MCU & IC Architecture Repo

## Scope

Document the internal architecture of selected semiconductors at varying depths.

### Primary Chips (Deep Documentation)

| Chip | Why Selected |
|------|-------------|
| **SI4735** | AM/FM/SW/LW tuner with DSP — maps both analog RF and digital signal processing internals |
| **ESP32-WROOM-32** | Dual-core Xtensa WiFi/BT SoC — maps CPU pipeline, wireless stacks, and rich peripheral subsystem |

### Secondary — Radio/Tuner ICs (Standard Documentation)

| Chip | Why Selected |
|------|-------------|
| SI4703 | FM-only tuner, no DSP — contrast with SI4735 |
| RDA5807 | Cheapest FM tuner — minimal entry point |
| RTL2832U | SDR demodulator — ties to SDR work |
| R820T2 | RF tuner front-end — pairs with RTL2832U |
| CC1101 | Sub-GHz transceiver — different frequency domain |

### Secondary — MCUs (Standard Documentation)

| Chip | Why Selected |
|------|-------------|
| ATmega328P | 8-bit AVR — Arduino Uno/Nano chip, simplest architecture |
| RP2040 | Dual ARM Cortex-M0+ — PIO state machines, modern design |
| STM32F103 | ARM Cortex-M3 — "Blue Pill", entry-level ARM |
| ESP32-C3 | RISC-V single-core — architectural contrast with ESP32 Xtensa |

---

## Functional Requirements

1. **Primary chips**: Full register-level documentation, block diagrams, DSP/wireless internals, power analysis, working code examples, benchmarks.
2. **Secondary chips**: Overview, block diagram, pinout, key registers, 1–2 code examples each.
3. **Visual Representations**: Block diagrams (Draw.io), flowcharts (Mermaid), signal flow diagrams for every chip.
4. **Technical Accuracy**: All information sourced from official datasheets and technical reference manuals.
5. **Modularity**: Each chip is self-contained in its own folder — easy to add new chips.
6. **Comparative Analysis**: Side-by-side tables comparing similar chips (e.g., SI4735 vs SI4703 vs RDA5807).

## Non-Functional Requirements

1. **Accessibility**: Clear language suitable for engineers and students.
2. **Maintainability**: Consistent structure across all chip folders.
3. **Formats**: Markdown for text, Draw.io for diagrams, PNG exports for quick viewing.
4. **License**: MIT — open for community contributions.

## Documentation Standards

- Consistent file naming: `overview.md`, `architecture.md`, `pinout.md`, `registers.md`, `power.md`
- Primary chips add: `dsp_details.md` (SI4735), `wifi_bluetooth.md` / `security.md` (ESP32), `firmware.md`, `benchmarks/`
- Cross-references between related chips (e.g., SI4735 → SI4703 comparison)
- Every register description includes: name, address, bit fields, reset value, access type, description
- Every diagram has both source file (`.drawio`) and exported PNG

## Tools and Dependencies

- **Text**: Markdown (GitHub-flavoured)
- **Diagrams**: Draw.io (VS Code extension or web), Mermaid (inline)
- **Version Control**: Git
- **Build/Run Examples**: GCC ARM, ESP-IDF, Arduino IDE, avr-gcc (chip-dependent)
- **Optional**: Logic analyser, oscilloscope for verification

## Future Enhancements

- Interactive block diagram viewer (HTML/JS)
- Automated register map extraction from SVD files
- Power consumption measurement scripts
- Comparison dashboard across all chips
- Educational tutorials linking theory to silicon