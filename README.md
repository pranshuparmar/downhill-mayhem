# 🚵 DOWNHILL MAYHEM

A **free, browser-playable, fan-made tribute** to the golden age of PS2 arcade downhill
mountain-bike racing — one long point-to-point race down a two-kilometre mountain against
5 AI rivals, with mid-air tricks that charge a boost meter and fists that settle position
disputes.

> Fan-made tribute. **Not affiliated with Sony.** No original game assets used.
> Every model is built from Three.js primitives, every texture is canvas-generated,
> and every sound is synthesized at runtime with the Web Audio API.

## Play it

- **Locally:** just double-click `index.html`. (It needs internet access once, to fetch the
  Three.js library from its CDN — everything else is inside the file.)
- **Hosted:** deploy to GitHub Pages (steps below) and share the link.

The whole game is a single self-contained `index.html` — no build step, no npm, no server.

## Controls

| Input | Action |
|---|---|
| `↑` / `W` | Pedal |
| `↓` / `S` | Brake |
| `←` `→` / `A` `D` | Steer |
| `Space` | Bunny hop — hop right at a ramp lip for bonus air |
| `Z` `X` `C` | Tricks while airborne: No Hander / Superman / Heel Clicker |
| `Shift` | Boost (drains the meter tricks fill) |
| `E` or `F` | Punch a nearby rider off their bike |
| `R` | Restart the race |
| `M` | Mute audio |
| `T` | Toggle the CRT scanline/vignette filter |

**How it plays:** the slope does most of the accelerating — pedal out of the gate and out of
slow corners, brake before the sweepers, and hit the wooden kickers for airtime. Start a trick
in the air and *land after it finishes* to bank boost meter; land mid-trick and you eat dirt.
Chain tricks in one jump for bonus meter. Rivals will shove and punch when you ride close —
punch first. Races are decided in the final third; rubber-banding keeps the pack honest.

## Deploy to GitHub Pages (step by step)

1. Create a **public** repository on GitHub (e.g. `downhill-mayhem`).
2. Upload `index.html` and `README.md` to the repository root — dragging and dropping the two
   files into the GitHub web UI ("Add file → Upload files") is fine. Commit to `main`.
3. In the repository, open **Settings → Pages**.
4. Under **Source**, choose **"Deploy from a branch"**.
5. Pick branch **`main`** and folder **`/ (root)`**, then click **Save**.
6. Wait a minute or two. The game goes live at:

   ```
   https://<your-username>.github.io/<repo-name>/
   ```

That's it — no Actions, no build configuration.

## Tech notes

- Single file: HTML + CSS + JS. Only external dependency is
  [Three.js r128](https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js)
  (classic global-script build, so it also works from `file://`).
- Seeded procedural course (~2 km, average ~13% grade) — the same track every run:
  sweeping turns, steep chutes, step-down drops and a set of wooden jump ramps.
- Riders simulate in track space (distance-along-course, lateral offset, height) and are
  converted to world space for rendering; terrain, physics and scenery all share one
  analytic ground function.
- PS2-era look on purpose: chunky flat-shaded low-poly terrain with vertex colours,
  aggressive distance fog, instanced pine trees and boulders, blob shadows, and an optional
  CRT scanline overlay.
- Zero accounts, zero ads, zero analytics, zero external calls beyond the Three.js CDN.

### Out of scope for v1 (kept in mind for later)

Multiple tracks, career mode, character select, multiplayer, touch/gamepad input,
persistence. The code is organized in sections (track / physics / AI / HUD / audio)
so these can be added without a rewrite.

## License

Original code, released under the terms in [LICENSE](LICENSE).
