# Serious Sam Classic VR - Work in progress
[![Support](https://img.shields.io/badge/Support-Donate-2ea44f?style=flat)](https://boosty.to/skyrimus)
[![Boosty](https://img.shields.io/badge/Boosty-Devlogs-F15F2C?style=flat)](https://boosty.to/skyrimus)
[![Telegram](https://img.shields.io/badge/Telegram-News-26A5E4?style=flat)](https://t.me/serious_sam_classic_vr)
[![YouTube](https://img.shields.io/badge/YouTube-Videos-FF0000?style=flat)](https://www.youtube.com/@Skyrimus)
[![Discord](https://img.shields.io/badge/Discord-Community-5865F2?style=flat)](https://discord.gg/SW3cF6Wn8N)

<table>
  <tr>
    <td width="50%">
      <img src="https://github.com/user-attachments/assets/1bb01ab9-5afe-4dd5-b5bb-7e8ebb5fec29" width="100%" />
    </td>
    <td width="50%">
      <img src="https://github.com/user-attachments/assets/98b5265a-9d5e-45a0-ba6a-f253b626d535" width="100%" />
    </td>
  </tr>
  <tr>
    <td width="50%">
      <img src="https://github.com/user-attachments/assets/e4341875-d126-42a2-8a62-1c7f8511da72" width="100%" />
    </td>
    <td width="50%">
      <img src="https://github.com/user-attachments/assets/2e5663ab-642e-4a57-956f-b3fa5ea21861" width="100%" />
    </td>
  </tr>
</table>

**The original Serious Sam Classics TFE & TSE in standalone VR, Windows PCVR, and flat-screen play, with cross-platform co-op.**

> **Status:** Work in progress. I am actively developing and testing the port.
>
> **An unofficial fan project by [Skyrimus](https://github.com/Skyrimus).**

[Project's Telegram channel](https://t.me/serious_sam_classic_vr) | [YouTube](https://www.youtube.com/@Skyrimus) | [Development updates on Boosty](https://boosty.to/skyrimus) | [Discord](https://discord.gg/SW3cF6Wn8N) | [Support development](https://skyrimus.ru/donate/)

## About

I started **Serious Sam Classic VR Port** in August 2025 to bring **Serious Sam Classic: The First Encounter (TFE)** and **The Second Encounter (TSE)** to standalone VR. My goal is to preserve what makes the original games special: fast combat, huge enemy encounters, original levels, jump pads, custom gravity, and the classic Serious Sam feel.

This project is based on the **original classic games**, not the HD remakes or Croteam's official VR editions. It builds on my earlier [Serious Sam Android Edition](https://github.com/Skyrimus/Serious-Sam-Android) work and uses **OpenXR** for standalone VR on Android-based headsets and for Windows PCVR. Standalone play runs directly on the headset, without PC streaming.

Although the project began as a VR port, its scope has grown. Current development builds also support **Android and Windows flat-screen play and cross-platform multiplayer**, so VR and non-VR players can share the same game. I have demonstrated cooperative play between a **standalone Pico 4** and a **Windows flat-screen client**. A separate **Linux amd64 dedicated-server target** supports headless hosting.

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
| **Windows - flat-screen** | ✅ Supported, tested |
| **Windows PCVR / SteamVR** | ✅ Supported, tested on Windows SteamVR |
| **Linux amd64 - dedicated server** | Headless build target; server hosting only |

The current Android branch supports both standalone VR and flat-screen play. The earlier Android phone port has its own [repository and installation instructions](https://github.com/Skyrimus/Serious-Sam-Android); use the instructions for your specific build, as its APK and data paths may differ from that older port.

Android and Windows builds support **Vulkan and OpenGL-based rendering**. Vulkan is enabled by default in the current build scripts. Graphics backend selection does not change which game or platform a build targets.

### Gameplay

- [Original VR teaser](https://www.youtube.com/watch?v=vCwtQk_FRE4)
- [Playlist Serious Sam Classic VR port](https://www.youtube.com/watch?v=HgV0xvwzQ_w&list=PL5C4uBtLzJuqzNQn7xSWyYn_7nfkWLl0r)
- [Cross-platform co-op - Pico 4 side](https://www.youtube.com/watch?v=HgV0xvwzQ_w)
- [Cross-platform co-op - Windows side](https://www.youtube.com/watch?v=Y3A6u_xINIk)
- [More videos on my YouTube channel](https://www.youtube.com/@Skyrimus)

## Features

### The original campaigns

- **Both The First Encounter and The Second Encounter are playable from beginning to end** in my development builds.
- A **shared VR/OpenXR implementation for TFE and TSE**, using the original classic game data.
- The original gameplay systems remain intact, including large enemy battles, jump pads, gravity changes, and level-specific mechanics.
- **Lua 5.4 scripting** for custom gameplay and map logic, with bindings for entities, world events, sound, and assets.
- I want to retain support for classic custom maps and mods wherever possible. Some community content may need additional work to function correctly in VR.

### VR movement and interactions

- **Native room-scale VR** with tracked head and controllers through OpenXR, on standalone Android headsets and Windows PCVR.
- **Smooth walking, teleportation, and hybrid locomotion**, with a teleport arc and destination preview. Smooth movement can follow the headset or left controller direction.
- **Configurable snap turning**, keeping the character and camera orientation synchronized.
- **Optional comfort vignette** that fades peripheral vision while walking.
- **Optional full-body avatar with inverse kinematics (Full Body IK)**, with an alternative weapons-and-hands view.
- **Head collision handling** to prevent looking through walls and other level geometry.
- **Physical interactions** with supported environmental objects, including buttons and levers.
- **Interactive Serious Bomb:** hold the bomb in one hand, hold a lighter in the other, and ignite the fuse by bringing them together.

My goal is to make the classic mechanics feel natural in VR without turning Serious Sam into a different game.

### VR weapons and HUD

- **Configurable weapon hand modes**, including dual wielding and a support-hand grip for compatible weapons.
- **Optional weapon weight and inertia**, with steadier handling when using a support-hand grip.
- **Motion-based knife attacks**, using the tracked blade movement to detect swings and hits.
- **Animated weapon hands**, including animations adapted for the shotgun and sniper rifle.
- **A rendered view through the sniper scope**, with adjustable scope resolution and quality settings.
- **A radial 3D weapon selector with a controller pointer**, ammunition rings, and an unread NETRICSA message counter.
- **Weapon-mounted ammunition indicators** and a **wrist HUD for health and armor**.
- **Optional weapon laser visuals** and **controller haptics with adjustable intensity**.

### VR menus and settings

- **World-space menus and NETRICSA panels**, operated with a tracked controller pointer.
- **A dedicated main-menu environment** and access to world-space menus during gameplay.
- **In-game VR settings** for locomotion, comfort mode, body and weapon hand modes, render scale, MSAA, scope resolution, particle limits, UI scale, world scale, weapon scale, and vibration.
- **An in-game cheat menu** adapted for use in VR.

### Rendering and performance

Running Serious Sam's large encounters at VR frame rates on standalone hardware requires changes throughout the engine. I have been reworking the renderer, asset handling, and CPU/GPU workload.

Current rendering features and optimizations include:

- **Vulkan rendering for Android and Windows, in both VR and flat-screen modes.** Vulkan is the default backend in the Android and Windows build scripts; **OpenGL ES 3 on Android and OpenGL 3.3 on Windows** remain supported alternatives.
- **OpenXR stereo rendering and Multiview**, reducing repeated rendering work between the two eyes, with per-eye rendering available as a fallback.
- **GPU-rendered particles and shader-based fog**, plus instancing and batching for repeated effects and objects.
- **Mesh instancing** for repeated geometry and selected enemy models, along with caching and batching of world geometry.
- **Skeletal-model rendering on Vulkan**, alongside the classic model rendering path.
- **Occlusion-related optimizations** and improvements to lens flares, lighting, shadows, and color reproduction.
- **Separate sniper-scope rendering**, with resolution and update-rate controls, plus optimizations to model preparation and HUD rendering.
- Improvements to loading and memory handling using **PhysFS**, **zstd**, **mimalloc**, and **meshoptimizer**, with **Tracy Profiler** for performance analysis.
- **Configurable particle limits**, helping balance visual effects and performance on standalone hardware.

I am continuing to profile and optimize the game. Performance depends on the device, level, settings, and development build; this README is not intended as an FPS benchmark.

### Cross-platform multiplayer

**Cross-platform co-op between standalone Android/OpenXR VR and Windows flat-screen clients is implemented in development builds.** I have demonstrated it between Pico 4 and Windows:

- [Pico 4 / Android OpenXR perspective](https://www.youtube.com/watch?v=HgV0xvwzQ_w)
- [Windows flat-screen perspective](https://www.youtube.com/watch?v=Y3A6u_xINIk)

The current networking implementation includes:

- **Server-authoritative replication**, enabled by default, with the server managing gameplay state across clients.
- **ENet-based network transport**.
- **Replication of XR head and controller poses, weapon selection, and weapon presentation**, so other players can see VR movement and equipment.
- **A separate headless Linux amd64 dedicated-server target**, without a graphics or OpenXR requirement.

Multiplayer continues to receive synchronization and stability fixes. Public client distribution, supported player counts, connection instructions, and compatibility with unmodified Steam executables will be documented with the relevant builds.

## Development status

**As of 17 October 2026:**

- Both classic campaigns are playable from start to finish in development builds.
- Standalone Android VR, Windows PCVR, and Android / Windows flat-screen modes are implemented; a separate Linux amd64 headless dedicated-server target is available.
- Vulkan is the default renderer in the Android and Windows build scripts, with OpenGL-based alternatives retained.
- VR features include teleport and hybrid locomotion, a comfort vignette, world-space menus and NETRICSA, animated weapon hands, and a wrist HUD.
- Cross-platform multiplayer uses server-authoritative replication and ENet, including XR pose and weapon replication. Windows flat-screen / Pico standalone-VR co-op has been demonstrated.
- I am continuing hardware compatibility, performance, interaction, and multiplayer synchronization and stability work.
- Public downloads and installation instructions for the current VR branch will be announced separately as appropriate.

For the latest updates, builds, and test announcements, follow the [Telegram channel](https://t.me/serious_sam_classic_vr).

## Development updates and videos

- [Telegram — project news, test announcements, and updates](https://t.me/serious_sam_classic_vr)
- [Boosty — development updates and devlogs](https://boosty.to/skyrimus)
- [YouTube — gameplay videos and development demonstrations](https://www.youtube.com/@Skyrimus)

## Installation and game data

I will provide installation instructions for each public build when it is ready. **Until then, use the instructions distributed with the specific test build you have received**; package names, file paths, and requirements may change during development.

Choose the **TFE or TSE build** for the game you want to play, and supply the original game data from a legitimate copy of that game:

- [**Serious Sam Classic: The First Encounter**](https://store.steampowered.com/app/41050/Serious_Sam_Classic_The_First_Encounter/)
- [**Serious Sam Classic: The Second Encounter**](https://store.steampowered.com/app/41060/Serious_Sam_Classic_The_Second_Encounter/)

Each build uses its matching game's data; you do not need to own both games to play one of them. Android uses the standard **TFE** and **TSE** builds for both Vulkan and OpenGL ES. Changing the graphics backend preserves the selected game's package identity and data directory.

**I do not distribute the original commercial game assets.** This project targets the classic game data, not the HD remakes.

For the older flat-screen Android version, visit [Serious Sam Android Edition](https://github.com/Skyrimus/Serious-Sam-Android).

## Credits and acknowledgements

**Created and developed by [Skyrimus](https://github.com/Skyrimus).**

**Mapping and level work:** [Mr.OgurchickT_T](https://t.me/VanyaLetov).

Special thanks to:

- **Croteam** for Serious Sam and Serious Engine.
- **Mr.OgurchickT_T** for support during the early stages of development.
- **Kliptexx** for Lua 5.4 integration collaboration.
- **Bazar** for the VR hand models used outside full-body IK mode.
- **ZCaliptium** for the Serious Bomb and lighter models and effects adapted from an earlier community mod.
- Everyone who helps test the game, reports problems, shares feedback, or supports development.

[Telegram](https://t.me/serious_sam_classic_vr) | [Discord](https://discord.gg/SW3cF6Wn8N) | [YouTube](https://www.youtube.com/@Skyrimus) | [Boosty](https://boosty.to/skyrimus) | [Support](https://skyrimus.ru/donate/)

## Disclaimer

**Serious Sam Classic VR Port is an unofficial fan project**.
Serious Sam, Serious Engine, and related trademarks and assets belong to their respective owners. I do not bundle copyrighted commercial game data with the project. Source-code licenses and third-party notices are provided with the relevant source distributions.
