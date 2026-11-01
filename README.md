# Omochi ESP32 OTA staging

Public static host for **signed OTA test artifacts only**. The source repository remains private.

## Current state

No firmware, manifest, or checksum artifact is published yet. Do not configure a device to update from this host until a signed candidate has been manually reviewed, uploaded, and verified to return HTTP 200 without redirects.

## Publication contract

The only expected files at the Pages root are:

- `manifest.json`
- `muse-gadget.bin`
- `SHA256SUMS`

All content here is publicly downloadable. Never publish source code, private signing keys, device tokens, Wi-Fi credentials, NVS data, logs, or personal information. Firmware updates must pass the device's compiled-in signature verifier; HTTPS alone is not sufficient.
