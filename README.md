# VIDVEC LIVE

Real-time browser-based motion vector visualisation. Captures live webcam input and renders directional vector lines on a pure black canvas using optical flow algorithms — all running entirely in the browser via OpenCV.js WASM.

**[Try the Live Demo](#)** (coming soon)

![License](https://img.shields.io/badge/license-MIT-green)
![Version](https://img.shields.io/badge/version-1.0.0-blue)

## Overview

VIDVEC LIVE is the real-time companion to [VIDVEC](https://github.com/MushroomFleet/VIDVEC) (batch mode). Where the batch tool processes pre-recorded video files, VIDVEC LIVE connects directly to your webcam and visualises motion vectors as they happen — frame by frame, in real time.

The output is a minimal, high-contrast display: white (or angle-coloured) vector lines drawn over a black background, representing the direction and magnitude of detected motion. An optional **Color Burn Overlay** mode composites the vector map on top of the original camera feed, revealing the source image only where motion is detected.

## Features

- **Two optical flow algorithms** — Sparse Lucas-Kanade (feature tracking) and Dense Farneback (flow field arrows)
- **Adjustable FPS targeting** — 1–60 FPS with preset buttons for Analysis (5), Standard (15), Smooth (30), and Max (60)
- **Color Burn Overlay mode** — composites vectors over the original input using Color Burn blending with configurable megapixel resolution normalization
- **Angle-based colouring** — optional HSL colour mapping from vector direction
- **Live recording** — capture the output canvas to WebM video directly in the browser
- **Snapshot export** — save individual frames as PNG
- **Mirror output** — flip the display horizontally for natural webcam mirroring
- **Performance meter** — real-time FPS, frame time, and load ratio monitoring
- **Camera switching** — select between connected cameras on the fly
- **Fully client-side** — no server, no uploads, all processing happens locally in your browser

## How It Works

```
Webcam → Video Frame → Optical Flow (OpenCV WASM) → Vector Map → Canvas Output
                                                          ↓
                                              [Optional: Color Burn
                                               composite with input]
```

1. The webcam feed is captured via the MediaStream API
2. Each frame is converted to grayscale and passed to OpenCV.js
3. Optical flow is computed between consecutive frames, producing motion vectors
4. Vectors are filtered by magnitude and rendered as directional lines
5. When Color Burn Overlay is enabled, the vector layer is composited over the original input frame using Canvas2D `color-burn` blending

## Settings

| Parameter | Range | Description |
|---|---|---|
| Algorithm | Sparse LK / Flow Arrows | Lucas-Kanade feature tracking or Farneback dense flow |
| Target FPS | 1–60 | Frame processing rate target |
| Max Features | 10–2000 | Maximum tracked points (sparse only) |
| Min Magnitude | 0–10 | Minimum vector length to display |
| Length Scale | 0.5–20 | Visual length multiplier for vectors |
| Max Line px | 5–200 | Maximum drawn line length in pixels |
| Grid Step | 4–64 | Sampling grid spacing (dense only) |
| Line Thickness | 1–5 | Stroke width for vector lines |
| Reseed Interval | 5–120 | Frames between feature re-detection (sparse only) |
| Colour by Angle | On/Off | HSL colouring based on vector direction |
| Mirror Output | On/Off | Horizontal flip for webcam mirroring |
| Color Burn Overlay | On/Off | Composite vectors over original input |
| Output MP | 0.1–2.0 | Resolution target in megapixels (overlay mode) |

## Tech Stack

- **React 18** with TypeScript 5
- **Vite 5** build tooling
- **OpenCV.js** (WASM) via `@techstark/opencv-js` for optical flow computation
- **Tailwind CSS 3** for styling
- **Canvas2D API** for rendering and compositing

## Links

- **Source Code:** [github.com/MushroomFleet/djz-vidvec-live](https://github.com/MushroomFleet/djz-vidvec-live)
- **Live Demo:** [Coming Soon](#)
- **Batch Mode (VIDVEC):** [github.com/MushroomFleet/VIDVEC](https://github.com/MushroomFleet/VIDVEC)

## 📚 Citation

### Academic Citation

If you use this codebase in your research or project, please cite:

```bibtex
@software{vidvec_live,
  title = {VIDVEC LIVE: Real-time Browser-based Motion Vector Visualisation},
  author = {Drift Johnson},
  year = {2025},
  url = {https://github.com/MushroomFleet/djz-vidvec-live},
  version = {1.0.0}
}
```

### Donate:

[![Ko-Fi](https://cdn.ko-fi.com/cdn/kofi3.png?v=3)](https://ko-fi.com/driftjohnson)
