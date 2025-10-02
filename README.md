# W-MBus
implementation should take an encrypted telegram and produce the correctly AES-128 decrypted payload, including the necessary metadata handling (e.g., IV, key usage, decryption mode).
# W-MBus Telegram Decryptor (OMS Volume 2)

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![C++17](https://img.shields.io/badge/C++-17-blue.svg)](https://isocpp.org/)
[![mbedTLS](https://img.shields.io/badge/crypto-mbedTLS-green)](https://github.com/Mbed-TLS/mbedtls)

Decrypt **Wireless M-Bus (W-MBus)** telegrams encrypted with **AES-128-CCM** according to the **OMS (Open Metering System) Volume 2 specification** (Security Mode 5).

> 🔒 **Compliance**: Fully implements OMS v2 Security Mode 5 nonce construction and authentication.

## ✨ Features
- Correct **12-byte nonce (IV) construction** from W-MBus header fields:
  - Device ID (4 bytes)
  - Manufacturer (2 bytes)
  - Version (1 byte)
  - Type (1 byte)
  - Access Number (4 bytes: ACC + `00 00 00`)
- Automatic hex string normalization (ignores spaces, newlines, case)
- MIC (Message Integrity Code) validation
- Dual output: **hex dump** + **printable ASCII**
- Clear error diagnostics for common issues

## 📦 Dependencies
- **C++17** compiler (`g++` ≥ 7 or `clang++` ≥ 5)
- **mbedTLS** ≥ 2.0 (`libmbedtls-dev`)

### Install Dependencies (Ubuntu/Debian)
```bash
sudo apt update && sudo apt install build-essential libmbedtls-dev
