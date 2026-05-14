# Tondro Rife Firmware Distribution

Public firmware distribution repository for the Tondro Rife ESP32 controller.

The iPhone app checks `manifest.json` to compare the connected controller firmware and app software against the latest published versions.

## Files

- `manifest.json`: Update metadata consumed by the iPhone app.
- `firmware/`: Versioned ESP32 firmware binaries.
- `signatures/`: Detached firmware signatures for secure OTA verification.

## Release Flow

1. Build the ESP32 firmware binary from the Arduino project.
2. Save the binary as `firmware/TondroRifeController-vX.Y.Z.bin`.
3. Generate its SHA-256 digest.
4. Sign the binary or digest with the Tondro firmware signing key.
5. Update `manifest.json` with version, size, SHA-256, signature URL, and release notes.
6. Commit and push to the public GitHub repository.

The ESP32 should reject OTA firmware that does not match the manifest hash/signature.
