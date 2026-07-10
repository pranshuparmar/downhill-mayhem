# 🚵 DOWNHILL MAYHEM

A **free, browser-playable, fan-made tribute** to *Downhill Domination* (PS2, 2003) —
one long point-to-point race down a mountain against 5 AI rivals, with mid-air tricks
that charge a boost meter and fists (and boots) that settle position disputes.

<p align="center">
  <a href="https://pranshuparmar.github.io/downhill-mayhem/">
    <img src="media/demo.gif" alt="Ten seconds of DOWNHILL MAYHEM: hitting a ramp, throwing a Superman, boosting, and punching a rival off their bike" width="600">
  </a>
  <br>
  <b><a href="https://pranshuparmar.github.io/downhill-mayhem/">▶ PLAY NOW — free, in your browser</a></b>
</p>

> Fan-made tribute. **Not affiliated with Sony** or the original developers.
> No original game assets are used: every model is built from Three.js primitives,
> every texture is canvas-generated, and every sound is synthesized at runtime with
> the Web Audio API.

## Play it

- **In your browser:** [pranshuparmar.github.io/downhill-mayhem](https://pranshuparmar.github.io/downhill-mayhem/)
- **Locally:** just double-click `index.html`. (It needs internet access once, to fetch
  the Three.js library from its CDN — everything else is inside the file.)

The whole game is a single self-contained `index.html` — no build step, no npm, no server.

## Controls

| Input | Action |
|---|---|
| `↑` / `W` | Pedal |
| `↓` / `S` | Brake |
| `←` `→` / `A` `D` | Steer |
| `Space` | Bunny hop — hop right at a ramp lip for bonus air |
| `Z` `X` `C` | Tricks while airborne: No Hander / Superman / Heel Clicker |
| `Shift` | Boost (drains the meter) |
| `E` | Punch a nearby rider off their bike |
| `F` | Kick — also works mid-air, and air strikes pay bonus boost |
| `R` | Restart the race |
| `M` | Mute audio |
| `T` | Toggle the CRT scanline/vignette filter |

**How it plays:** the mountain does most of the accelerating — pedal out of the gate and
out of slow corners, brake before the sweepers, and hit the wooden kickers for airtime.
Start a trick in the air and *land after it finishes* to bank boost meter; land mid-trick
and you eat dirt. Chain tricks in one jump for bonus meter, and clean riding trickles
meter in on its own — crashing dumps most of it. The groomed line is fastest, but the
whole hillside is rideable: rollers, dirt patches and slalom trees open up alternate
lines. Rivals shove, punch and kick when you ride close — swing first (`E`/`F`), and
land a mid-air kick for an AIR STRIKE bonus. Races are decided in the final third;
rubber-banding keeps the pack honest. Riders get fresh jersey colours every race.

## Tech notes

- Single file: HTML + CSS + JS. Only external dependency is
  [Three.js r128](https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js)
  (classic global-script build, so it also works from `file://`).
- Seeded procedural course (~2.3 km, ~16% average grade) — the same mountain every run:
  sweeping turns, steep chutes, step-down drops, wooden kickers, and a broad rolling
  hillside around the racing line.
- Riders simulate in track space (distance-along-course, lateral offset, height) and are
  converted to world space for rendering; terrain, physics and scenery all share one
  analytic ground function.
- PS2-era look on purpose: chunky flat-shaded low-poly terrain with vertex colours,
  aggressive distance fog, instanced pine trees and boulders, blob shadows, and an
  optional CRT scanline overlay.
- Zero accounts, zero ads, zero analytics, zero external calls beyond the Three.js CDN.
