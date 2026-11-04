# Omochi ESP32 OTA staging

Public static host for **signed OTA test artifacts only**. The source repository remains private. Everything under this Pages site is publicly downloadable.

## Current OTA candidate

- Firmware: `1000.0.1` (`ai-fortune-ideaspark`, classic ESP32 Rev 1.1+, 16 MB Flash)
- Manifest: [manifest.json](https://heron-note.github.io/omochi-esp32-ota-staging/manifest.json)
- Image: [muse-gadget.bin](https://heron-note.github.io/omochi-esp32-ota-staging/muse-gadget.bin)
- SHA-256: `7678e15167113a5473c38273b008f73d1e7d7f82b4527b6a60347e8a271a6406`
- Image size: 1,638,388 bytes (OTA slot capacity: 2 MiB)
- Signatures: manifest ECDSA P-256/SHA-256 and ESP-IDF Secure Boot V1-compatible ECDSA P-256 image signature independently verified.

The initial serial bootstrap is `1000.0.0`; it is intentionally older than this staging OTA candidate. The package and instructions for that bootstrap are delivered separately. This candidate has **not** been confirmed on physical hardware: serial bootstrap, link health gate, OTA installation, and rollback remain to be tested on the actual board.

## Publication contract

The active OTA payload at the Pages root consists of `manifest.json`, `muse-gadget.bin`, and `SHA256SUMS`. Never publish source code, private signing keys, device tokens, Wi-Fi credentials, NVS data, logs, or personal information. Firmware updates must pass the device's compiled-in signature verifier; HTTPS alone is not sufficient. The manifest and firmware are served from this same HTTPS origin and must return direct HTTP 200 responses without redirects.
