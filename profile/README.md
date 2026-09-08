# CRITICAL INFORMATION:
**Architectural Alignment and Hardening is currently taking place... please do not consume the ESPressio Development Platform until this message has been removed!**

In order to make ESPressio Development Platform (EDP) fully stable and production-ready, an extensive process is underway at this time to:
- Finalise the overall architecture of the current ESPressio feature-set
- Perform exhaustive optimisations across the entire suite of Platform Libraries
- Ensure Abstraction is fully maturated, and that now architecture/device-specific calls or references remain in the downstream ESPressio libraries (all such cases will become consumers of the `ESPressio System` library, which itself is being extended to translate hardware/system-specific references/calls into ESPressio-generic language).
- Ensure maximum stability across ESP32 devices, specifically targeting the ESP32 Pico as the lowest supportable chipset target.
- Soak test every feature, including Saturation Testing for transmission, reception, and processing of each Core Primitive (Command, Event, State)

To put it simply: we're making the ESPressio Development Platform (EDP) production ready and hardened!

As part of this process, the exceptional decision has been made to withdraw all previous releases (all of which have been pre-production releases for internal testing) and - once the process is complete - release every ESPressio library as a new 1.0.0 initial, production-ready and hardened release!

During this time, it is sensible for you to not consume any ESPressio libraries in your own code, as we will be breaking a lot of interfaces, moving a lot of code between libraries (abstracting), and performing full-suite integration tests at an extremely rapid rate.

The process was aiming to complete sooner (29th August 2026), however, tests and audits have uncovered significant optimisations that simply MUST be implemented before we can honestly consider ESPressio ready for production environments... and so we shall continue until this work is completed.

The current target completion date is: **Saturday, 12th September 2026**
<!--
# ESPressio Development Platform
## Designed for ESP32 - with every intention to grow beyond!
ESPressio Development Platform (EDP) is designed specifically to abstract the complexities of foundational hardware implementation from _your_ Application code.

EDP achieves this by taking care of the following complexities for you, while providing an easy-to-understand abstraction interface (API) against which your own Application's code can consume:
- Threads: enables your Applications to leverage the full power of its underlying Microcontroller, without the need for your code to make a single hardware-level instruction call or reference!
- Events: enables your Applications to decouple logic, and operate Asynchronously, simply by defining a suitable Event Type to contain relevant information, dispatch it through ESPressio's integrated Event Engine, then for separate modules of your code to operate against these dispatched Events at their own discretion. **Events can be transmitted across Sockets and even across multiple Devices via Network and/or Radio!**
- 
-->
