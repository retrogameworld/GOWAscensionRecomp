# Changelog (project milestones)

## 2026-11-16
- Sewer camera stutter fixed: swizzled 16-bit float textures decoded on the GPU (bit-exact, no fps cost).
- Freeze guards ported from BilalReloaded's port (GCM label window, report validation).
- In-game PC Settings entry now follows the game's own Options screen (Options only, instant, no overlap).
- Transition-barrier elision: chapter 17 lowest second 58 → 70 fps.
- Native render-job stages; shader precompile screen on a cold driver cache.
- Release gate: 10 recorded routes at 4K/120, no second below 60 fps on the release build.

## 2026-11-15
- Leaner indirect calls and PPU build options: Heca200 at 4K/120 101 → 109 fps.
- Thread pinning from 8 s: first Continue after boot runs pinned (lowest second 55 → 67).
- Balcony-fall hitch fixed (cloth settle 2 frames instead of 5).
- PC Settings zoom into the title-screen gear rock.

## 2026-11-14
- Native EDGE job and native RenJobSet render job, exact against the lifted code.
- Chained-fight sound timing fixed.

## 2026-11-10 – 2026-11-11
- Ground-slam burst snapped and tilted to the ground on stairs.
- Golden door shadow sawtooth smoothed (soft shadows above 1x) and shimmer reduced.
- Optional HD intro movie and logos; crisper subtitles.
- Parallel cloth resets at loads.

## 2026-11-09
- Every EDGE plugin lifted to native code (chapter 20: 36 fps → playable).
- PS3-style Delete Profile prompt.
- Megaera phase-400 dip analysed; 8 SPUs.

## 2026-11-07 – 2026-11-08
- 120 Hz game logic.
- 4K fixes: white sky, glow on chain/blades, speckled face, subtitles and text.
- Logos and movies at 4K/120.
- "Delete this saved data?" confirmation.
