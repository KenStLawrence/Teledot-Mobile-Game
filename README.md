# Teledot-Mobile-Game
Teledot is a minimalist reflex survival game built in Construct 3. It was designed as a small, shippable prototype to demonstrate rapid tool onboarding, clean game-feel, and end-to-end delivery (playable release on itch.io).

Play: [itch.io link here]  
Trailer / GIF: [link here]  
Platform: HTML5 (desktop + mobile browser)

## What it is
You control a player dot by teleporting to your cursor/touch position. Red hazards fall from above and the pace ramps over time. Survive as long as possible.

## Why I built it
This was my first complete game, intentionally scoped to be understandable and finishable: one core mechanic, one clear fail state, high polish per minute of content. The goal was to prove I can:
- learn a new engine fast (Construct 3),
- design a readable loop,
- implement clean state-driven logic,
- ship a playable build (itch),
- and then move on to larger projects with the same execution standard.

## Core mechanics
- **Teleport movement** (mouse or touch) with screen clamping for consistent feel.
- **Escalating difficulty** driven by survival time.
- **Hazard spawning** using an accumulator-based spawner (stable across frame rates).
- **Score/feedback**: time survived + teleport count (“tele/teles”).

## UX & polish systems
- **State machine** with `"TITLE"`, `"PLAY"`, `"DEAD"` driving all major behavior.
- **Death sequence**: collision triggers slow-motion time scale, staged reveals, and restart lockout.
- **Tween-driven UI**: fade-in/out sequencing for title, game over, score, and “tap to continue”.
- **Afterimage trail** on teleport for readability and motion feel.
- **Visual effect control**: layer effect parameter modulation (warp ripple “trip” pulses during play).
- **Audio controls**: mute toggle + track skip / auto-advance when a track ends.

## Implementation notes (high level)
- Input mode switches between `"MOUSE"` and `"TOUCH"` to keep control logic simple.
- Difficulty increases over time via `gdiff = gtime / 10` and `spawnrate = grate + gdiff * 5`.
- Spawning uses `spawnacc += spawnrate * dt` then spawns when `spawnacc >= 1`, subtracting 1 each spawn.
- Restart is protected by `grestartlock` to prevent accidental instant resets during the death sequence.

## Build & run
- Open the project in Construct 3.
- Export as HTML5 for itch.io (web).
- Recommended: include a short gameplay GIF in the repo + a link to the itch build.

## Roadmap
- Mobile app store packaging (Android/iOS) once the publishing pipeline is prioritized.
- Monetization hooks (ads / IAP) if appropriate for platform.
- Content expansion (variants, skins, additional hazard patterns, modifiers).
- Lightweight meta progression (optional) without bloating the core loop.

## Credits
Design, code, UI/UX: Ken St. Lawrence 
Engine: Construct 3  
Audio: [credit or “original / licensed” here]
