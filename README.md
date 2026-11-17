# God of War: Ascension - native PC recompilation (project info)

A static recompilation of **God of War: Ascension** (PS3, US version **BCUS98232**, update **1.12**) to native **Windows x64**.
The game's PPU and SPU code is translated to C/C++ and compiled natively; the PS3 GPU (RSX) command stream is rendered with Direct3D 12.

> **This repository holds information about the project only.**
> It contains **no source code, no game code, no game data and no firmware.**
> Running the recomp requires your own legally obtained copy of the game, its official update and the PS3 firmware files.

---

## Highlights

- **4K** output (internal resolution scale 3x), also 1080p and 1440p.
- **120 Hz game logic** (`run_120hz.cmd`) and a smooth **60 Hz** mode (`run_60hz_smooth.cmd`).
- **PC Settings menu**
  - On the title screen: the gear rock (Triangle → PC Settings), plus an Exit Game entry.
  - In game: *(Triangle) PC Settings* on the Options screen; settings apply at once and are saved to `gowa_settings.ini`.
- **Frame generation options:** AMD FSR 3 frame generation, and it works alongside NVIDIA Smooth Motion. AMD FSR 3.1 upscaling is in progress.
- **Shader precompile screen** on a cold driver shader cache (after a driver update or a rebuild), instead of minutes of stutter.
- **HD textures** for selected assets (the Hecatonchires hands, arm and skin; the guardhouse creature), plus optional HD intro movie and logos.
- **Optional cheats:** god mode, one-hit kills, infinite magic.
- **Low-end launcher** (`run_lowend.cmd`).

## Performance

Measured on a Ryzen 9 9950X3D + RTX 5080, 4K, 120 Hz mode, recorded-input bench routes (release gate of the 2026-11-16 evening build):

| Route | Average fps | Lowest 1-second fps | Seconds below 60 |
|---|---|---|---|
| Heca200 (grapple, AI) | 114 | 80 | 0 |
| Megaera phase 400 | 107 | 75 | 0 |
| Chapter 17 | 100 | 64 | 0 |
| Chapter 20 trial wave | 85 | 66 | 0 |
| Sewers | 119 | 85 | 0 |
| Golden door | 116 | 83 | 0 |
| Chapter 1 opening | 118 | 85 | 0 |
| Options / PC Settings | 112 | 86 | 0 |
| Beetle swarm | 106 | 70 | 0 |
| Checkpoint 234 | 118 | 86 | 0 |

The heaviest fight wave (chapter 20) varies between runs; one run in three had a single second at 56 fps.

## In progress

- **"Glory to Eros" scene:** a black/dark-panel flicker during the fade-in (being traced draw by draw) and an fps dip to ~55-61 caused by the EDGE geometry jobs saturating their SPUs.
- **Hecatonchires ladder walk:** uneven frame pacing (camera judder) from the same EDGE wait.
- **Beetle swarm:** a short freeze when the sound banks are relocated.
- **First-visit shader storms:** a temporary stand-in shader while the exact one compiles.
- AMD FSR 3.1 upscaling, NVIDIA DLSS/DLAA (later).

## How it works (short)

1. The decrypted executable is lifted function by function to C (PPU) and the SPU programs to C++, with game-specific passes.
2. HLE replaces the PS3 system libraries (GCM, SPURS, audio, pad, file system, saves).
3. The RSX command stream is translated to Direct3D 12 at run time; shaders are decompiled to HLSL and cached.
4. Everything is compiled with Clang (AVX-512 or AVX2 builds).

## Credits and licenses

- AMD FidelityFX SDK (MIT) for FSR 3 frame generation.

## Legal

This is a non-commercial fan project, not affiliated with or endorsed by Sony Interactive Entertainment or Santa Monica Studio.
*God of War* is a trademark of Sony Interactive Entertainment. No copyrighted game content is distributed here.
