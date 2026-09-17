# CRITICAL INFORMATION:
**This platform is under serious active development, and is NOT ready for production use!**

The changes being prepared right now are designed to not only harden the platform, but to ensure that it meets extremely strict memory allocation constraints across the broadest possible scope of ESP32 variants.

This work is not easy, but the goal is to ensure that an application can be built using the full ESPressio platform stack, on the smallest possible ESP32 variant.

To meet the minimum acceptance criteria for full public (production-worthy) release, the minimum required stack must include:
- Primitives:
  - Command (at least 5 concurrently registered with Transmission support bindings)
  - Event (at least 5 concurrently registered with Transmission support bindings)
  - State (at least 5 concurrently registered with Transmission support bindings)
- Radio (one of, minimum):
  - Raw 802.11
  - BLE
  - NRF24
- Mesh (with minimum of)
  - 20 concurrent Nodes supportable
  - Clock Synchronisation to <1ms precision
- WiFi
  - AP until Client mode (runs as its own Access Point until connected as a Client to another WiFi Access Point)
- Web
  - Web UI
  - WebSocket with support for all Primitives
  - REST API host (with support for all Primitives)
- Persisted Configuration Storage (and retreival)
- OTA Updates
  - Full failsafe rollback in the event of power loss or update failure
  - Full verification of firmware metadata and binary to ensure applicability and legitimacy before being accepted for update
  - Means to obtain updates from:
    - File upload via Web UI
    - Propagation of Firmware Updates via Mesh (transmission and reception)
    - Obtain from Web Server over HTTP/HTTPS
    - Any valid Binary Stream as a source (regardless of transport)

Once these conditions are met on (in the VERY LEAST) the original ESP32-WROOM-32 MCU, with stability and reliability, the platform will be considered ready for a production release.

Meanwhile, feel free to follow this post, the repositories, our official Discord channel, and our official Instagram channel to stay updated on our progress.
