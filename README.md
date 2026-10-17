# Serious Sam Classic VR - Work in progress
[![Support](https://img.shields.io/badge/Support-Donate-2ea44f?style=flat)](https://skyrimus.ru/donate/)
[![Boosty](https://img.shields.io/badge/Boosty-Devlogs-F15F2C?style=flat)](https://boosty.to/skyrimus)
[![Telegram](https://img.shields.io/badge/Telegram-News-26A5E4?style=flat)](https://t.me/serious_sam_classic_vr)
[![YouTube](https://img.shields.io/badge/YouTube-Videos-FF0000?style=flat)](https://www.youtube.com/@Skyrimus)
[![Discord](https://img.shields.io/badge/Discord-Community-5865F2?style=flat)](https://discord.gg/SW3cF6Wn8N)

**The original Serious Sam Classics TFE & TSE in standalone VR, with cross-platform gameplay beyond VR.**

> **Status:** Work in progress. I am actively developing and testing the port.
>
> **An unofficial fan project by [Skyrimus](https://github.com/Skyrimus).**

[Project's Telegram channel](https://t.me/serious_sam_classic_vr) | [YouTube](https://www.youtube.com/@Skyrimus) | [Development updates on Boosty](https://boosty.to/skyrimus) | [Discord](https://discord.gg/SW3cF6Wn8N) | [Support development](https://skyrimus.ru/donate/)

## About

I started **Serious Sam Classic VR Port** in August 2025 to bring **Serious Sam Classic: The First Encounter (TFE)** and **The Second Encounter (TSE)** to standalone VR. My goal is to preserve what makes the original games special: fast combat, huge enemy encounters, original levels, jump pads, custom gravity, and the classic Serious Sam feel.

This project is based on the **original classic games**, not the HD remakes or Croteam's official VR editions. It builds on my earlier [Serious Sam Android Edition](https://github.com/Skyrimus/Serious-Sam-Android) work and uses **OpenXR** for native VR support on Android-based headsets, without PC streaming.

Although the project began as a VR port, its scope has grown. I am also working on **flat-screen platform support and cross-platform multiplayer**, so VR and non-VR players can share the same game. I have already demonstrated cooperative play between a **standalone Pico 4** and a **Windows flat-screen client**.

The name *VR Port* reflects the project's origins; it no longer describes every part of what I am building. **OpenXR is used for VR, while flat-screen clients do not require OpenXR.**

## Platforms

Here is where development and testing currently stand. **A platform appearing in this table does not mean its latest build is available for download.**

| Platform / mode | Status |
| --- | --- |
| **Pico 4 - standalone VR** | ✅ Supported, tested, my primary development and testing headset |
| **Pico 4 Ultra - standalone VR** | ✅ Supported, tested |
| **Meta Quest 2 - standalone VR** | ✅ Supported, tested |
| **Meta Quest 3 - standalone VR** | ✅ Supported, tested |
| **Meta Quest 3S - standalone VR** | ✅ Supported, tested |
| **Android phones - flat-screen** | ✅ Supported, tested |
| **Windows - flat-screen** | ✅ Supported, tested via Pico 4 and Windows flat build |
| **Windows PCVR / SteamVR** | ✅ Supported, tested on Windows SteamVR |

The Android phone port has its own [repository and installation instructions](https://github.com/Skyrimus/Serious-Sam-Android). Please do not assume that the old Android APK or its file paths are interchangeable with the current VR build.

### Gameplay

- [Original VR teaser](https://www.youtube.com/watch?v=vCwtQk_FRE4)
- [Playlist Serious Sam Classic VR port](https://www.youtube.com/watch?v=HgV0xvwzQ_w&list=PL5C4uBtLzJuqzNQn7xSWyYn_7nfkWLl0r)
- [Cross-platform co-op - Pico 4 side](https://www.youtube.com/watch?v=HgV0xvwzQ_w)
- [Cross-platform co-op - Windows side](https://www.youtube.com/watch?v=Y3A6u_xINIk)
- [More videos on my YouTube channel](https://www.youtube.com/@Skyrimus)

## Features

### The original campaigns

- **Both The First Encounter and The Second Encounter are playable from beginning to end** in my development builds.
- I maintain a shared VR/OpenXR implementation for the classic **TFE 1.05** and **TSE 1.07** engine branches.
- The original gameplay systems remain intact, including large enemy battles, jump pads, gravity changes, and level-specific mechanics.
- I want to retain support for classic custom maps and mods wherever possible. Some community content may need additional work to function correctly in VR.

### VR gameplay and interactions

- **Native room-scale VR** with tracked head and controllers through OpenXR.
- **Optional full-body avatar with inverse kinematics (Full Body IK)**, with the option to use a simpler weapon-only view.
- **Physical interactions** with supported environmental objects, including buttons and levers.
- **Interactive Serious Bomb:** hold the bomb in one hand, hold a lighter in the other, and ignite the fuse by bringing them together.
- **VR-adapted weapon selection and HUD**, including ammunition indicators attached to weapons.
- **Configurable snap turning**, keeping the character and camera orientation synchronized.
- **Head collision handling** to prevent looking through walls and other level geometry.
- **In-game cheat menu** and adaptations to classic menus and gameplay interactions.

My goal is to make the classic mechanics feel natural in VR without turning Serious Sam into a different game.

### Rendering and performance

Running Serious Sam's large encounters at VR frame rates on standalone hardware requires changes throughout the engine. I have been reworking the renderer, asset handling, and CPU/GPU workload rather than simply adding stereo cameras to the original PC version.

Key areas of work include:

- **OpenXR stereo rendering and Multiview**, reducing repeated rendering work between the two eyes.
- A modernized **OpenGL ES** rendering path for Android VR.
- **GPU particles and fog**, as well as instancing and batching for repeated effects and objects.
- **Mesh instancing** for repeated geometry and selected enemy models.
- **Occlusion-related optimizations** and improvements to lens flares, lighting, shadows, and color reproduction.
- Optimizations for **sniper-scope rendering**, model preparation, loading, memory allocation, and the HUD.
- Engine improvements using **PhysFS**, **zstd**, **mimalloc**, and **meshoptimizer**, with **Tracy Profiler** for performance analysis.
- Device-specific fixes for **Meta Quest 2 and Quest 3**, including an OpenXR frame-rendering issue and reduced particle workload on Quest 2.

I am continuing to profile and optimize the game. Performance depends on the device, level, and development build; this README is not intended as an FPS benchmark.

### Cross-platform co-op

I have demonstrated **cross-platform cooperative gameplay between Pico 4 (standalone Android/OpenXR VR) and Windows (flat-screen)**:

- [Pico 4 / Android OpenXR perspective](https://www.youtube.com/watch?v=HgV0xvwzQ_w)
- [Windows flat-screen perspective](https://www.youtube.com/watch?v=Y3A6u_xINIk)

This is still **experimental multiplayer functionality**. I am working on stability and compatibility before treating it as a finished public feature. Details such as public client distribution, supported player counts, connection instructions, and compatibility with unmodified Steam executables will be documented when they are ready.

**A Windows flat-screen client is not the same thing as a completed Windows PCVR / SteamVR port.**

## Development status

**As of 17 October 2026:**

- Both classic campaigns are playable from start to finish in development builds.
- I am continuing VR compatibility and performance work for Pico and Meta Quest hardware.
- I have demonstrated Windows flat-screen / Pico standalone-VR co-op.
- I am improving platform support, interaction systems, and multiplayer stability.
- Public downloads and installation instructions for the current VR branch will be announced separately as appropriate.

For the latest updates, builds, and test announcements, follow the [Telegram channel](https://t.me/serious_sam_classic_vr).

## Development updates and videos

### Devlogs

- [Project's Telegram channel](https://t.me/serious_sam_classic_vr)

## Installation and game data

I will provide installation instructions for each public build when it is ready. **Until then, use the instructions distributed with the specific test build you have received**; package names, file paths, and requirements may change during development.

You need the original game data from a legitimate copy of:

- [**Serious Sam Classic: The First Encounter**](https://store.steampowered.com/app/41050/Serious_Sam_Classic_The_First_Encounter/)
- [**Serious Sam Classic: The Second Encounter**](https://store.steampowered.com/app/41060/Serious_Sam_Classic_The_Second_Encounter/)

**I do not distribute the original commercial game assets.** This project targets the classic game data, not the HD remakes.

For the older flat-screen Android version, visit [Serious Sam Android Edition](https://github.com/Skyrimus/Serious-Sam-Android).

## What's next

I am currently focusing on:

- Improving performance and stability across Pico and Meta Quest devices.
- Refining VR controls, interactions, and compatibility with both classic campaigns.
- Expanding testing and improving stability of cross-platform multiplayer.
- Improving compatibility with classic custom maps and selected community mods.
- Evaluating additional platforms, including potential PCVR support.
- Preparing clear build and installation documentation as releases become available.

These are development priorities, **not promised release dates or a fixed feature schedule**.

## Credits and acknowledgements

**Created and developed by [Skyrimus](https://github.com/Skyrimus).**

**Mapping and level work:** [Mr.OgurchickT_T](https://t.me/VanyaLetov).

Special thanks to:

- **Croteam** for Serious Sam and Serious Engine.
- **Mr.OgurchickT_T** for support during the early stages of development
- **Kliptexx** for Lua 5.4 integration collaboration
- **Bazar** for models of XR Hands models used in non-full body mode
- **ZCaliptium** for the Serious Bomb and lighter models and effects adapted from an earlier community mod.
- Everyone who helps test the game, reports problems, shares feedback, or supports development.

[Telegram](https://t.me/serious_sam_classic_vr) | [Discord](https://discord.gg/SW3cF6Wn8N) | [YouTube](https://www.youtube.com/@Skyrimus) | [Boosty](https://boosty.to/skyrimus) | [Support](https://skyrimus.ru/donate/)

## Disclaimer

**Serious Sam Classic VR Port is an unofficial fan project**.
Serious Sam, Serious Engine, and related trademarks and assets belong to their respective owners. I do not bundle copyrighted commercial game data with the project. Source-code licenses and third-party notices are provided with the relevant source distributions.
