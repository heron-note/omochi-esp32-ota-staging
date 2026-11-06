# Omochi ESP32 OTA staging

Public static host for **signed OTA test artifacts only**. The source repository remains private. Everything under this Pages site is publicly downloadable.

## Current OTA test candidate

- Firmware: `1000.0.3` (`ai-fortune-ideaspark`, classic ESP32 Rev 1.1+, 16 MB Flash)
- Intended starting firmware: USB-installed `1000.0.2`
- Manifest: [manifest.json](https://heron-note.github.io/omochi-esp32-ota-staging/manifest.json)
- Image: [muse-gadget.bin](https://heron-note.github.io/omochi-esp32-ota-staging/muse-gadget.bin)
- SHA-256: `0b91722b5718597815765cb94b0954b68017d4ccc406d37389fe3c46395e58e7`
- Image size: 1,638,388 bytes (OTA slot capacity: 2 MiB)
- Signatures: manifest ECDSA P-256/SHA-256 and ESP-IDF Secure Boot V1-compatible ECDSA P-256 image signature independently verified.
- The image version descriptor, board profile, minimum chip revision 1.1, image size, SHA-256, and manifest schema were independently checked.

The device's previously shared heartbeat after USB installation showed `ws=up` continuously for more than 230 seconds. The actual OTA request and update have **not yet been run**. Once requested from Muse using `device.ota` with no parameters, the expected verification is download and signature/hash validation, automatic reboot, running version `1000.0.3`, and post-boot health-gate success. OTA rollback has not yet been demonstrated.

## Publication contract

The active OTA payload at the Pages root consists of `manifest.json`, `muse-gadget.bin`, and `SHA256SUMS`. Never publish source code, private signing keys, device tokens, Wi-Fi credentials, NVS data, logs, or personal information. Firmware updates must pass the device's compiled-in signature verifier; HTTPS alone is not sufficient. The manifest and firmware are served from this same HTTPS origin and must return direct HTTP 200 responses without redirects.
