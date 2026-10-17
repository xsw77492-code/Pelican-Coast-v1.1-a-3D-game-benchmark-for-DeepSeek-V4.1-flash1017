# Pelican Coast

### One HTML file. Zero dependencies. A 3D game built to test DeepSeek-V4.1-flash1017.

> On the surface, it is a pelican riding a bicycle into a golden-hour coastline.  
> Under the hood, it is a **232 KB, zero-dependency, single-file capability test** — built, shipped, and tested in a real browser.

[简体中文](README.md) · **English**

<p align="center">
  <img alt="Model: DeepSeek-V4.1-flash1017" src="https://img.shields.io/badge/model-DeepSeek--V4.1--flash1017-4f6df5?style=flat-square">
  <img alt="Renderer: native WebGL2" src="https://img.shields.io/badge/renderer-native%20WebGL2-2f9e8f?style=flat-square">
  <img alt="Zero dependencies" src="https://img.shields.io/badge/dependencies-0-f0a45e?style=flat-square">
  <img alt="Single HTML file" src="https://img.shields.io/badge/build-single%20HTML-ef8f72?style=flat-square">
  <img alt="Version v1.1" src="https://img.shields.io/badge/version-v1.1-e98f72?style=flat-square">
  <img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-f3a47c?style=flat-square">
</p>

![Pelican Coast title screen](screenshots/cover.jpg)

## Why this exists

In October 2026, we put the new **DeepSeek-V4.1-flash1017** through a deliberately unforgiving test:

> “Make a small HTML game about a pelican riding a bicycle. It can be 3D. Let the player control speed and dodge obstacles.  
> The animation and interface must be beautiful. The algorithms must be accurate.”

There was one extra rule:

**No Three.js. No game engine. No external images, audio, or font files. Everything in one HTML file.**

We were not testing whether the model could produce a plausible-looking demo. We were testing whether it could deliver **creative direction, 3D graphics, collision math, procedural art, game feel, UI, audio, responsive design, and engineering polish** in one pass.

This is the result: a straw-hatted pelican with a silk scarf, riding a teal bicycle through a low-poly sunset.

**Vibe-coded. Then tested like it wasn't.**

> [!NOTE]
> This is an independent evaluation project, not an official DeepSeek project. The model name follows this run's evaluation configuration.

## The 30-second version

| | |
| --- | --- |
| Artifact | One `index.html`, about **232 KB**, zero runtime dependencies |
| Rendering | **Native WebGL2** with a hand-written math, shader, mesh, and particle stack |
| Gameplay | Three lanes, speed control, fish pickups, combos, near misses, three hearts |
| Visuals | Procedural sunset coast, pelican rider, animated silk scarf, ocean, palms, lighthouse |
| Platforms | Keyboard on desktop, touch controls on mobile, fully offline |
| Model | **DeepSeek-V4.1-flash1017** (this run) |
| Verified | 60.2 FPS · 0 console errors · 35 obstacle rows with 0 fairness failures · mobile pass |

## Play it

**Local:** download or clone the repo, then open [`index.html`](index.html). No install, no build, no internet required.

Or serve the folder:

```bash
python -m http.server 8080
```

Then open <http://localhost:8080/>.

**GitHub Pages:** after pushing to GitHub, go to `Settings → Pages → Deploy from a branch`, choose `main` and `/ (root)`, then play at:

```text
https://<your-username>.github.io/pelican-coast/
```

> [!TIP]
> Chrome or Edge with WebGL2 enabled gives the best experience.

## Controls

| Action | Keyboard |
| --- | --- |
| Accelerate | `W` / `↑` |
| Brake / slow down | `S` / `↓` / `Space` |
| Change lane | `A` `D` / `←` `→` |
| Pause / resume | `P` / `Esc` |
| Mute | `M` |
| Restart after game over | `R` / `Enter` |

Touch devices automatically get left/right lane buttons, `slow`, and `go`.

## Screenshots

![Gameplay](screenshots/gameplay.jpg)

<p align="center">
  <img src="screenshots/near-miss.jpg" width="100%" alt="Near miss and combo feedback">
</p>

## What is in the game

- **Three-lane speed runner**: dodge barriers, crates, and traffic cones while managing speed.
- **Near misses**: squeeze past an obstacle for bonus points, combo, gold particles, and a whoosh.
- **Combo chain**: fish and near misses build a combo. Miss the 4.5-second window and it drops; hit an obstacle and it resets instantly.
- **Combo scoring**: higher combo multiplies all score, shown live in the HUD and recorded as max combo at the end of a run.
- **Three hearts**: collisions cost a heart, slow the bike, and grant brief invincibility.
- **Complete game loop**: title screen, countdown, play, pause, death, results, restart, local best score.
- **Procedural coast**: animated ocean, sunset sky, palms, lighthouse, sailboats, birds, floating particles.
- **Rebuilt pelican**: longer S-curved neck, feather collar, folded wing feathers, tail fan, wide straw hat with flowers, silk scarf, rear bouquet.
- **Desktop and mobile**: the same single file adapts to both, with touch controls on coarse pointers.

## Why this is a hard model test

The hard part is not drawing a pelican.

- **No library crutches**: no Three.js, no engine, no ready-made game template.
- **3D math**: camera, projection, lighting, normals, matrices, and swept collision are implemented from scratch.
- **Procedural art**: the coast, sky, pelican, bicycle, hat, scarf, and flowers are all code.
- **Algorithmic correctness**: the generator cannot create an obstacle row with no reachable safe line.
- **Complete state machine**: intro, countdown, play, pause, damage, death, results, restart, persistence.
- **Performance and responsiveness**: 60 FPS on desktop, playable at 375 px wide.
- **Taste**: consistent palette, composition, silhouette, and animation — the part that is hardest to grade automatically.
- **It has to actually run**: not just look like game code.

## Evaluation results

The full test log is in [EVALUATION.md](EVALUATION.md) (Chinese), with an English summary below.

| Check | Result |
| --- | --- |
| Delivery | Single file, zero runtime dependencies, zero external assets |
| Ready time | ~0.9 s |
| Gameplay FPS @ 1440×900 | **60.2 FPS** |
| Console errors | **0** |
| WebGL errors | **0** |
| Obstacle fairness | **35 rows, 0 unreachable safe lines** |
| Near-miss detection / score / VFX | Pass |
| Combo build / 4.5 s expiry / hit reset | Pass |
| Max combo in results | Pass |
| Collision → heart loss → death → results | Pass |
| Pause / resume / restart | Pass |
| Best score in `localStorage` | Pass |
| Mobile 390 / 375 layouts | Pass, no horizontal overflow |
| Mobile touch lane change | Pass |

Environment:

```text
Chrome + WebGL2
ANGLE / Direct3D 11
Intel UHD Graphics
1440 × 900 / 60.2 FPS
```

## v1.0 → v1.1

This project was not a one-shot demo that was abandoned after generation.

- **v1.0** delivered the coast, the rider, the game loop, the UI, audio, and mobile support.
- **v1.1** added combo and near-miss gameplay, rebuilt the pelican model after feedback, and added a browser regression pass.

That iteration matters for a model evaluation: it tests not only first-pass generation, but whether the model can revise a working artifact, preserve correctness, and improve the experience.

## Technical notes

<details>
<summary><strong>Open the engine notes</strong></summary>

- **Hand-written WebGL2 renderer**: matrix math, perspective projection, custom mesh builder, GLSL shaders, and a fixed render loop.
- **Procedural geometry**: the pelican, bicycle, obstacles, palms, lighthouse, coastline, and fish are generated at boot.
- **Animated silk scarf**: a custom cloth mesh updated every frame, with motion driven by speed, steering, and time.
- **Fixed 120 Hz simulation**: rendering and gameplay are decoupled. Even at low frame rates, movement does not tunnel through thin obstacles.
- **Swept collision**: each obstacle is tested against the rider using the Z interval swept during the step.
- **Fair obstacle generation**: at most two lanes are blocked per row; every safe lane from the previous row must be reachable with at most one lane change.
- **Procedural audio**: ocean, wind, pickups, collisions, near misses, combo milestones, countdown, and results are synthesized with WebAudio.
- **Responsive rendering**: capped device pixel ratio on small screens and a dedicated touch layer.
- **Local persistence**: best score and mute preference use `localStorage`.

</details>

## Reproduce the test with another model

If you want to compare coding models:

1. Give the model the same constraints: **one file, zero dependencies, zero external assets, complete game, beautiful animation, accurate collision and obstacle generation**.
2. Ask for a plan before implementation.
3. Open the result in a real browser — do not review code alone.
4. Run the fairness check: can every previous safe lane reach a safe lane in the next row?
5. Test collisions at both high and low frame rates, plus pause, death, restart, and mobile.
6. Record the outcome in [EVALUATION.md](EVALUATION.md) or submit a PR.

### Debug API

The page exposes a test-only object, `window.__pelicanCoast`:

```js
window.__pelicanCoast.getState();          // state, combo, fairness log
window.__pelicanCoast.start();
window.__pelicanCoast.skipCountdown();
window.__pelicanCoast.advance(5);          // fast-forward 5 seconds
window.__pelicanCoast.setSpeed(24);
window.__pelicanCoast.setInvincible(999);  // tests / demos only
window.__pelicanCoast.moveLane(1);
window.__pelicanCoast.stageNearMiss();     // controlled near-miss scenario
window.__pelicanCoast.pause();
window.__pelicanCoast.resume();
```

This is not a stable public API; it exists for automated screenshots and gameplay verification.

## Roadmap

- **v1.2**: daily seeded challenge, more obstacle types, 60-second sprint mode
- **v1.3**: unlockable bike paints, hats, and scarf colors
- **Later**: ghost replays, more coastlines, multi-model comparison write-ups

## Contributing

Contributions are welcome:

- test another model and share the result
- improve gameplay, visuals, or performance
- report a bug or propose a cleaner implementation
- use the project as a reference for single-file games or coding-model evaluations

For pull requests, please try to preserve the **single-file, zero-dependency, offline-playable** nature of the project.

## License

[MIT](LICENSE) © 2026 xu-shiwei66

---

### ⭐ If this is useful

If you evaluate coding models, build single-file games, or just like a pelican on a bicycle, **a star helps more people discover this benchmark**.

**Tested with DeepSeek-V4.1-flash1017 · Built in DeepSeek Harness · Independent project, not affiliated with DeepSeek.**
