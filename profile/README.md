# Update - Tuesday October 6th 2026 -

You may have noticed a number of ESPressio libraries are once again publicly visible.
This is because the platform is moving forwards at a considerable pace, with the new (considerably faster, more efficient, less memory-intensive) Mesh system entering its final lab testing stage today... with public release expected this week!

Testing is taking place on a laboratory testing system providing 20x ESP32-WROOM-32 Development Boards, 2x M5StickC-Plus 2 development devices, 2x M5Stack StopWatch (ESP32-S3) devices, and - eventually - 8x Arduino Nano development boards fitted with NRF24 radio modules.
The objective is to provide full, multi-modal *seamless* Mesh connectivity, with consistent performance and full sub-millisecond clock synchronisation across not only devices, but across architectures as well.

The newly-published ESPressio libraries already massively outperform the original libraries (which were withdrawn for the sake of this fundamental platform redevelopment, with its new - fully bounded - architecture) in both compute speeds *and* memory utilisation requirements. They do far more while using far less memory!

For the first time, the Localisation platform has also been published for public use. This enables you to not only provide language-localised Strings for international users, but eliminates the need to embed Strings in your program itself! This reduces memory requirements as well as the size of your binaries.

A lot is coming up... so stay tuned for more updates, or join our Discord channel if you want to discuss things actively.

# Update - Sunday 27th September 2026 -

Considerable progress has been made with the full architectural redevelopment of ESPressio!

You will notice that a significant number of the libraries are now public again (with their new `EDP-*` prefixing) and these comprise much of the core platform facilities.

They also introduce entirely new functionality, tested and proven to work exactly as desired.

However... the 1.0.0 release is not yet ready. This is because there are a number of other libraries in development right now, some of which include the `Application` layer (which itself provides `Application Mode`, enabling you to easily and intuitively produce Applications which can operate in different modes depending on your needs... including OTA Update mode, Diagnostics Mode - should you require one - the standard operating mode, and any other modes you may need).
The idea is that your Application will Bootstrap the components it requires to operate in any given Mode, in the correct order, and exclude anything that the given Application Mode does not require.

At the same time, the `Primitive` types (`Command`, `Event`, `State` and a new type called `Request` - which is specifically designed to ask for any available participating Node on a Mesh to perform a discrete unit of processing, allowing your Application to distribute its workload based on available Idle Capacity across an entire Mesh) are being actively developed and prepared for imminent release.

In parallel, the Radio and Mesh libraries are being redeveloped against the new Architecture.

There is still much to be done, but progress is being made, the pace is accelerating, and we look forward to demonstrating the complete Platform very soon.

# Update - Wednesday 23rd September 2026 -

The feature set for the V1 release has now been decided (and, therefore, the final scope of initial development):

The libraries will soon start appearing to the public, in the order in which they achieve V1 completion. Thereafter, they will *remain* public, and their fundamental architecture will be considered "locked".

## The features include...

### Monotonic System Clock
Backed by a multitude of architecture/platform/hardware-specific providers.

### Synchronised System Clock
A means to synchronise a reference System Clock across hardware devices (e.g. via Radio, Socket, Mesh) with a Bootstrap-customisable Synchronisation Precision Target.
Safe-taming means that the System Clock is guaranteed to never step backward.

### Composition Framework
A powerful, compiler-backed way of injecting Concrete Implementations to satisfy Interfaces, without the need for a Runtime Type Directory, Dynamic Memory Allocation, or any non-deterministic mechanism.
The Composition Framework provides an extremely rich vocabulary for resolving the correct Type/Types to satisfy each Interface/Contract.

### Persistence
Store and load data from a multitude of sources: internal Flash storage, various external storage solutions (e.g. SD, MMC, eMMC etc.)

### Localised String Facility
A complete toolchain to build String Translation Tables, eliminating the need to embed Strings in binaries, the means to exchange numeric identifiers which resolve back to rational (localised) Strings across languages. This includes the toolchain to build the efficient Language Packs, as well as to resolve Strings from identifiers outside of the running Application.
This means that you can now emit extremely rich diagnostics and logging information within your Application, with significantly reduced memory consumption, and transcode those logs into human-readable complete messages in a local language.

### Type Serialisation/Deserialisation
Without RTTI!
Attribute-style Schema Metadata enables you to expand your Types with the capability of being Serialisable, and can marshal the corresponding type at Runtime, populating its values through Deserialisation.
This enables you to exchange complete Objects across Transmission Boundaries (Radio, Mesh, Sockets, CLI, WebUI etc.)

### Security & Encryption
A comprehensive library of Security and Encryption facilities for data at rest *and* in transit. Entropy, replay protection... all included.
Robust, hardware-backed implementations are included for Arduino and ESP32 devices.

### Threading and Tasking
Whether you require a well-managed, enduring Worker Thread, or an ad-hoc Task Runner... ESPressio Development Platform has what you're looking for!
- Carefully-bounded (Bootstrap-defined) Task Runner Pools
- Dedicated Worker Threads
- High-Precision Worker Threads (with nanosecond-resolution Delta calculations, scheduled execution, "good citizen" sleep behaviour when not working, wake-by-signal... all bolt-on capabilities available directly in the library!)

### Serialisable/Deserialisable Commands
Think beyond Device Boundaries! ESPressio Development Platform includes the facility to define asynchronous executable Commands, and each Command can be exposed for External Invocation (from outside of your Application, or even external to your device).
The rich Schema Language enables your Control Surfaces (e.g. CLI, WebUI etc.) to dynamically *compose* structured Commands, then dispatch them into your Application for execution.

### The Event Engine
Drive behaviour by fully-decoupled, cross-boundary Event Notifications.
Where a Command is an explicit instruction to do something, an Event is a notification that something happened (Event-Driven Observer Pattern).

It is no longer necessary for separate modules of your code to maintain references between each other (or even to know the other exists in the first place).

The Event *is* the contract!

Just as with Commands, Events can be exchanged across Application and Device boundaries... meaning that connected devices can emit and consume the same Event Types, over any Transport.
Radio, Mesh, CLI, WebUI, Sockets... however you need to exchange them, the library provides!

### Shared State
Define centralised State information (e.g. "LED1 is On" or "Door Accelerometer: Pos: X, Y, Z, Accel: X, Y, Z") as rich, Structured Types... and exchange them across Application and Device boundaries over any Transport.

This enables you to build extraordinarily sophisticated distributed systems, whose respective Application code can consume External State information indiscriminately from Local State information. The Transports take care of exchanging the information fro you... over Radio, Mesh, CLI, WebUI, Sockets... any supportable Transport technology.

### Intuitive Radio Communication
A carefully-designed, hardware-independent Radio Communication Interface enables your code to trivially communicate across devices.
- NRF24
- Raw 802.11 WiFi Radio (radio without Access Points)
- Bluetooth and BLE
- UART Radio modules
Best of all: Encryption and Security are *built-in!*

### The Mesh
A bespoke Mesh solution augments your devices' Radios with a fully secure (at least to Industry Standard), self-discovering, cross-technology Mesh topological connectivity.
- Clock Synchronisation across Devices
  - Automatic Reference-Client negotiation across all devices (each device will use its best possible Peer as its Reference, while itself potentially serving as Reference for one or more other Nodes when the software determines that it would be the most appropriate Reference for said Node(s))
  - Sophisticated Clock Taming ensures that the Synchronised Clock cannot go backwards (it will always progress forwards)
  - Robust Synchronisation Quality Reporting enables your code to differentiate between truly-synchronised time, "close synchronisation", and unsynchronised time.
- Native support for Commands, Events, and State. It's fully-integrated by design, so your Mesh devices can exchange everything they need to form a cohesive distributed solution.
- Multi-Radio Support! Each device can participate on the same Mesh using different Radios, so long as at least one reachable Node exposes a compatible Radio.
  - If any Node provides both Raw 802.11 Radio AND BLE, for example, while the majority of nodes only expose Raw 802.11 Radio... a node exposing only BLE can still participate in the Mesh (so long as it is within range of the existing Node providing both Raw 802.11 Radio AND BLE)
- Automated Session Control - if a Node restarts, the Mesh retains its State and it can - safely and securely - rejoin the Mesh under its new Session ("Incarnation")
- Full Encryption! Your Mesh is YOUR Mesh... no device without your cryptographic keys can intrude... this is a distinct advantage over some other solutions such as ESP-Now!
- Fully Portable! The entire ESPressio Development Platform is designed to support all potential architectures and hardware platforms... so not only ESP devices may participate in your Mesh!

# Update - Saturday 19th September 2026 -

As ESPressio matures towards it's first production-ready release incarnation, it is absolutely crucial that **nobody attempt to use the current, published, public ESPressio-\* libraries in any production-intended projects.**

Everything from the present publicly-visible libraries is going to be replaced by a new, stronger, consistent, and *fully deterministic* platform (the present repositories will ultimately be withdrawn and replaced).

The new platform follows an extremely robust design, which has been formulated over the past 3 months and is now being implemented.

The repositories containing the new design will become visible the moment that the first production-ready release is completed (hopefully within the next 2-3 weeks, I'll provide more concrete release expectations once I can reasonably be certain that they are achievable).

In the meantime, **do not build a dependency on the current, public ESPressio-\* libraries in this organisation.

# Update 2 - Saturday 19th September 2026 -

I have temporarily made private the ESPressio libraries to prevent anyone from inadvertently consuming them with their present interfaces (API), as the entire interface, API, and Bootstrap methodology is going to change on a fundamental level.
