# Omochi ESP32 OTA staging

Public static host for **signed OTA test artifacts only**. The source repository remains private. Everything under this Pages site is publicly downloadable.

## Current OTA test candidate

- Firmware: `1000.0.3` (`ai-fortune-ideaspark`, classic ESP32 Rev 1.1+, 16 MB Flash)
- Intended starting firmware: USB-installed `1000.0.2`
- Manifest: [manifest.json](https://heron-note.github.io/omochi-esp32-ota-staging/manifest.json)
- Image: [muse-gadget.bin](https://heron-note.github.io/omochi-esp32-ota-staging/muse-gadget.bin)
- SHA-256: `0b91722b5718597815765cb94b0954b68017d4ccc406d37389fe3c46395e58e7`
- Image size: 1,638,388 bytes (OTA slot capacity: 2 MiB)
- Manifest signature, ESP-IDF Secure Boot V1-compatible image signature, schema, embedded version, profile, chip revision, size, and hash were independently verified.

The USB-installed `1000.0.2` device has been observed with `ws=up` for more than 230 seconds. When OTA is enabled, the ESP32 firmware advertises `device.ota` in its dynamic `commands_v2` registration and has a `link.invoke` handler that starts OTA. A separate custom Muse-side integration may not be needed. However, actual command invocation from the user's Muse interface has not been tested. OTA has not started, and post-boot health gate and rollback remain untested. Do not assume that typing the literal text `device.ota` invokes the registered command.

## Publication contract

The active OTA payload at the Pages root consists of `manifest.json`, `muse-gadget.bin`, and `SHA256SUMS`. Never publish source code, private signing keys, device tokens, Wi-Fi credentials, NVS data, logs, or personal information. Firmware updates must pass the device's compiled-in signature verifier; HTTPS alone is not sufficient. The manifest and firmware are served from this same HTTPS origin and must return direct HTTP 200 responses without redirects.
