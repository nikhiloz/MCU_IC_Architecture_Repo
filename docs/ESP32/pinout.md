# ESP32 — Pinout (ESP32-WROOM-32 Module)

## GPIO Pin Map (38-pin DevKit)

| Pin | GPIO | Functions | ADC | Touch | Notes |
|-----|------|-----------|-----|-------|-------|
| 1 | GPIO0 | Boot mode select, PWM | ADC2_1 | T1 | Strapping pin (LOW = download) |
| 2 | GPIO1 | UART0 TX | — | — | Default serial TX |
| 3 | GPIO2 | Boot mode, LED on some boards | ADC2_2 | T2 | Strapping pin |
| 4 | GPIO3 | UART0 RX | — | — | Default serial RX |
| 5 | GPIO4 | General purpose | ADC2_0 | T0 | |
| 6 | GPIO5 | VSPI CS0 | — | — | Strapping pin |
| 7–12 | GPIO6–11 | SPI Flash (DO NOT USE) | — | — | Connected to flash |
| 13 | GPIO12 | HSPI MISO | ADC2_5 | T5 | Strapping pin (flash voltage) |
| 14 | GPIO13 | HSPI MOSI | ADC2_4 | T4 | |
| 15 | GPIO14 | HSPI CLK | ADC2_6 | T6 | |
| 16 | GPIO15 | HSPI CS0 | ADC2_3 | T3 | Strapping pin |
| 17 | GPIO16 | UART2 RX | — | — | Used by PSRAM on WROVER |
| 18 | GPIO17 | UART2 TX | — | — | Used by PSRAM on WROVER |
| 19 | GPIO18 | VSPI CLK | — | — | |
| 20 | GPIO19 | VSPI MISO | — | — | |
| 21 | GPIO21 | I2C SDA (default) | — | — | |
| 22 | GPIO22 | I2C SCL (default) | — | — | |
| 23 | GPIO23 | VSPI MOSI | — | — | |
| 24 | GPIO25 | DAC1 | ADC2_8 | — | |
| 25 | GPIO26 | DAC2 | ADC2_9 | — | |
| 26 | GPIO27 | General purpose | ADC2_7 | T7 | |
| 27 | GPIO32 | General purpose | ADC1_4 | T9 | |
| 28 | GPIO33 | General purpose | ADC1_5 | T8 | |
| 29 | GPIO34 | Input only | ADC1_6 | — | No internal pull-up/down |
| 30 | GPIO35 | Input only | ADC1_7 | — | No internal pull-up/down |
| 31 | GPIO36 (VP) | Input only | ADC1_0 | — | No internal pull-up/down |
| 32 | GPIO39 (VN) | Input only | ADC1_3 | — | No internal pull-up/down |

## GPIO Matrix

Unlike fixed-function MCUs, the ESP32 has a **GPIO Matrix** that allows flexible routing:

- Almost any peripheral signal can be mapped to any GPIO pin
- Exception: ADC, DAC, touch, and a few others are fixed to specific pins
- Configured via `gpio_iomux_in()` / `gpio_iomux_out()` or ESP-IDF GPIO driver

## Strapping Pins

These pins determine boot behaviour and must be at specific levels during reset:

| GPIO | Function | Boot (Download) | Boot (Flash) |
|------|----------|-----------------|--------------|
| GPIO0 | Boot mode | LOW | HIGH (default) |
| GPIO2 | Must be LOW for download | LOW | Don't care |
| GPIO5 | — | — | Default HIGH |
| GPIO12 | Flash voltage select | LOW (3.3V flash) | LOW |
| GPIO15 | Silence boot messages | LOW (silent) | HIGH (print) |

## Power Pins

| Pin | Description |
|-----|-------------|
| VIN / 5V | 5V input (regulated to 3.3V on-board) |
| 3V3 | 3.3V output (from on-board regulator) |
| GND | Ground (multiple pins) |
| EN | Enable (active high, pull low to reset) |

## Important Constraints

- **GPIO6–11**: Connected to SPI flash — do not use as general GPIO
- **GPIO34, 35, 36, 39**: Input-only, no internal pull-up/down
- **ADC2**: Cannot be used while WiFi is active (shared with WiFi radio)
- **GPIO16, 17**: Used by PSRAM on ESP32-WROVER modules

> TODO: Add visual pinout diagram in `diagrams/`
