# 🦋 Flying Butterflies

A real-time 3D butterfly simulation built with Three.js — no backend, no build tools, just a single HTML file.

**[✨ Live Demo](https://tengyanhaiin-star.github.io/Flying-Butterflies/)**

---

## Features

- **100 autonomous butterflies** flying freely inside a 3D bounding box
- **Realistic wing animation** — each butterfly flaps at 5 Hz with an independent phase offset, so they never look synchronized
- **Procedurally drawn wing textures** — vivid blue with black veins, white marginal dots, and red-orange eyespots on the hindwings, all painted on an HTML5 Canvas at runtime
- **Autonomous flight AI** — butterflies fly head-first, hover and turn when they hit a wall or another butterfly, and occasionally change direction spontaneously
- **Collision detection** — butterflies bounce off the walls and off each other with physically correct mirror-reflection
- **Orbit camera** — drag to rotate the view, scroll / pinch to zoom
- **iOS optimized** — single-finger rotate, two-finger pinch-to-zoom, reduced geometry and texture resolution for smooth performance on mobile

## Controls

| Input | Action |
|---|---|
| Drag (mouse / single finger) | Rotate camera |
| Scroll wheel / two-finger pinch | Zoom in / out |

## How It Works

### Wing Textures

All four wings share a single 1024 × 1024 Canvas texture (512 × 512 on iOS). The entire butterfly is drawn on one canvas in world coordinates, and each wing geometry's UV is manually remapped to match its position in that canvas — so there is no UV seam or mirroring problem between wings.

### Flight System

Each butterfly maintains an independent `flyDir` vector (the actual movement direction) and a `headYaw / headPitch` pair (the visual orientation). The head smoothly follows the flight direction with a lag, giving a natural look. When a butterfly hits a wall or another butterfly, the flight direction is mirror-reflected about the collision normal, and the butterfly enters a brief hover state while the head catches up.

### Performance

On desktop, 100 butterflies run at 60 fps. On iOS the count is automatically reduced to 30, antialiasing is disabled, and geometry subdivision is halved.

## Tech Stack

- [Three.js r128](https://threejs.org/) — 3D rendering
- HTML5 Canvas API — procedural wing textures
- Vanilla JavaScript — no framework, no build step

## License

MIT — see [LICENSE](LICENSE) for details.
