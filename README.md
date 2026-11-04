# Omochi ESP32 OTA staging

Public static host for **signed OTA test artifacts only**. The source repository remains private. Everything under this Pages site is publicly downloadable.

## Current candidate

- Firmware: `1000.0.0` (`ai-fortune-ideaspark`, classic ESP32 Rev 1.1+, 16 MB Flash)
- Manifest: [manifest.json](https://heron-note.github.io/omochi-esp32-ota-staging/manifest.json)
- Image: [muse-gadget.bin](https://heron-note.github.io/omochi-esp32-ota-staging/muse-gadget.bin)
- SHA-256: `20eae4d31bf93a5d290d876a3eaf009da4f3fb496e948e7accd1aa15a9f8e1b1`
- Image size: 1,638,388 bytes (OTA slot capacity: 2 MiB)
- Signatures: manifest ECDSA P-256/SHA-256 and ESP-IDF Secure Boot V1-compatible ECDSA P-256 image signature independently verified.

This is a **test candidate**, not a claim of successful physical-device OTA. It still requires serial bootstrap, real-board health-gate confirmation, and an OTA update from a newer candidate before the flow is accepted end to end.

## Publication contract

The OTA payload consists of `manifest.json`, `muse-gadget.bin`, and `SHA256SUMS`. Never publish source code, private signing keys, device tokens, Wi-Fi credentials, NVS data, logs, or personal information. Firmware updates must pass the device's compiled-in signature verifier; HTTPS alone is not sufficient. The manifest and firmware are served from this same HTTPS origin and must return direct HTTP 200 responses without redirects.
