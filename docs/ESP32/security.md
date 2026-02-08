# ESP32 — Security

## Security Features Overview

The ESP32 includes hardware-accelerated security features for secure boot, flash encryption, and cryptographic operations.

## Cryptographic Hardware Accelerators

| Accelerator | Algorithms | Performance |
|-------------|-----------|-------------|
| AES | 128/192/256-bit | Hardware, ~10× faster than software |
| SHA | SHA-1, SHA-256, SHA-384, SHA-512 | Hardware |
| RSA | Up to 4096-bit | Hardware, used for secure boot verification |
| ECC | ECDSA | Hardware |
| TRNG | True Random Number Generator | Hardware entropy source |

## Secure Boot

### Secure Boot V1 (ESP32 v1/v3 chips)
1. eFuse stores SHA-256 hash of signing key
2. ROM bootloader verifies second-stage bootloader signature
3. Second-stage bootloader verifies application signature
4. Chain of trust: ROM → Bootloader → Application

### Secure Boot V2 (ESP32 ECO3+)
- RSA-3072 based (stronger than V1)
- Supports key revocation (up to 3 keys)
- Signed metadata includes version field for rollback protection

### Enabling Secure Boot
```
idf.py menuconfig
# Navigate: Security features → Enable secure boot
# → Select boot verification mode
# → Generate signing key
```

## Flash Encryption

- AES-256 encryption of external flash contents
- Transparent decryption by hardware during read
- Protects firmware and data from physical extraction
- Development mode: allows re-flashing (limited count)
- Release mode: permanently locks encryption (no further plaintext writes)

### Flash Encryption Flow
```
┌──────────┐     ┌──────────────┐     ┌──────────┐
│ Plaintext│────►│ AES-256      │────►│ External │
│ Firmware │     │ Encryption   │     │ Flash    │
└──────────┘     │ (hardware)   │     │(encrypted│
                 └──────────────┘     └──────────┘
                                            │
                 ┌──────────────┐           │
                 │ AES-256      │◄──────────┘
                 │ Decryption   │ Transparent on read
                 │ (hardware)   │
                 └──────┬───────┘
                        ▼
                 ┌──────────────┐
                 │ CPU reads    │
                 │ plaintext    │
                 └──────────────┘
```

## eFuse Security Configuration

| eFuse | Purpose |
|-------|---------|
| JTAG_DISABLE | Disable JTAG debug interface |
| DIS_DOWNLOAD_MODE | Disable UART download mode |
| FLASH_CRYPT_CNT | Flash encryption enable/disable counter |
| ABS_DONE_0 | Secure boot V1 permanently enabled |
| ABS_DONE_1 | Secure boot V2 permanently enabled |
| KEY_PURPOSE_x | Purpose assignment for key blocks |

## OTA (Over-the-Air) Updates

- Dual partition scheme: OTA_0 and OTA_1
- New firmware written to inactive partition
- Verified before switching boot partition
- Rollback support if new firmware fails to boot
- Works with secure boot (new firmware must be signed)

## Security Considerations

- Once secure boot is enabled in release mode, it cannot be disabled
- Flash encryption has limited re-flash count in development mode
- JTAG can be permanently disabled via eFuse
- WiFi credentials stored in NVS should use NVS encryption
- BLE pairing uses Secure Connections (LESC) when available

> TODO: Add step-by-step secure boot and flash encryption setup guide
