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

# Update - Saturday 19th September 2026 -

As ESPressio matures towards it's first production-ready release incarnation, it is absolutely crucial that **nobody attempt to use the current, published, public ESPressio-\* libraries in any production-intended projects.**

Everything from the present publicly-visible libraries is going to be replaced by a new, stronger, consistent, and *fully deterministic* platform (the present repositories will ultimately be withdrawn and replaced).

The new platform follows an extremely robust design, which has been formulated over the past 3 months and is now being implemented.

The repositories containing the new design will become visible the moment that the first production-ready release is completed (hopefully within the next 2-3 weeks, I'll provide more concrete release expectations once I can reasonably be certain that they are achievable).

In the meantime, **do not build a dependency on the current, public ESPressio-\* libraries in this organisation.

# Update 2 - Saturday 19th September 2026 -

I have temporarily made private the ESPressio libraries to prevent anyone from inadvertently consuming them with their present interfaces (API), as the entire interface, API, and Bootstrap methodology is going to change on a fundamental level.
