# Aetheris — Organic Geometric Atmosphere (WebGL)

A single-file, zero-dependency interactive WebGL application that blends sacred harmonic geometry with procedural weather physics. Built using raw GLSL fragment shaders and an Apple-inspired glassmorphic UI, **Aetheris** renders counter-rotating concentric polygons warped by 2D Simplex noise alongside multi-layered, wind-sheared rain and surface ripples.

---

## ✨ Features

* **Procedural Sacred Geometry (GLSL):** Renders 9 concentric, counter-rotating rounded polygons whose sides, roundness, and organic vertex warping evolve continuously over time.
* **Multi-Layered Atmospheric Rain & Ripples:** Three parallax depth layers of wind-tilted rain streaks, expanding concentric surface ripples, and subtle sheet-lightning pulses during storms.
* **Interactive Pointer Physics:** Moving or dragging your cursor/finger bends the local wind shear and applies a gravitational lensing warp across the geometric field.
* **Smooth Exponential State Choreography:** Switching presets or adjusting sliders smoothly interpolates all shader uniforms (`u_wind`, `u_rain`, `u_complexity`, `u_stormMood`) at 60+ FPS.
* **Zero Build Step:** Packaged in a single self-contained HTML file (`index.html`) with inline GLSL shaders and Tailwind CSS via CDN.

---

## 🚀 Getting Started

Because **Aetheris** has no external asset dependencies or bundler requirements, you can run it immediately:

1. **Open Directly:** Double-click `index.html` to open it in any modern WebGL-capable browser (Chrome, Safari, Firefox, Edge).
2. **Or Serve Locally (Optional):**
   ```bash
   # Using Python 3
   python3 -m http.server 8080

   # Or using Node.js (npx)
   npx serve .
   ```
   Then visit `http://localhost:8080` in your browser.

---

## 🎛 Controls & Interaction

### Atmospheric Presets
* **☀ Clear Harmonic:** Warm amber and espresso tones, gentle rotational breathing, and zero precipitation.
* **🌦 Light Rain:** Introduces moderate wind shear, soft mist, light rain streaks, and delicate water ripples.
* **⛈ Dramatic Storm:** Shifts the palette to deep storm slate and bioluminescent cyan-silver with heavy diagonal rain, higher harmonic complexity, and distant sheet lightning.

### Fine-Tuning Sliders
| Control | Range | Effect |
| :--- | :--- | :--- |
| **Wind Shear** | `-30°` to `+30°` | Tilts the angle and velocity of falling rain streaks and sways outer geometric rings. |
| **Precipitation** | `0%` to `100%` | Scales rain streak density across all three parallax layers, surface ripple frequency, and storm mood. |
| **Harmonic Order** | `3.0` to `12.0` | Smoothly morphs the concentric polygons from triangles (`3`) to hexagons (`6`) up to dodecagons (`12`). |

### Pointer & Touch
* **Hover / Drag:** Warps the geometric rings around your pointer and dynamically nudges wind direction.
* **Controls Toggle (Top Right):** Collapses the bottom dock for an unobstructed full-screen ambient display.

---

## 🧠 Shader Architecture Overview

All visual rendering happens inside the `<script id="fragment-shader" type="x-shader/x-fragment">` block on a full-screen quad:

1. **2D Simplex Noise (`snoise`):** Generates smooth, organic coordinate distortion so rigid geometric rings breathe and flow naturally.
2. **Signed Distance Fields (`sdHarmonicPolygon`):** Evaluates continuous angular folding so fractional polygon side counts morph seamlessly without harsh jumps.
3. **Parallax Rain (`rainLayer`) & Ripples (`rippleLayer`):** Uses deterministic 2D hash functions (`hash12`, `hash22`) to spawn thousands of anti-aliased rain streaks and expanding 3×3 neighborhood water rings entirely on the GPU.
4. **Filmic Tone-Mapping & Dithering:** Applies an ACES-inspired soft shoulder curve and sub-pixel micro-dithering to eliminate color banding in dark atmospheric gradients.

---

## 🎨 Customization Ideas

* **Connect Live Weather Data:** Fetch real-time wind speed and precipitation from the free, no-auth [Open-Meteo API](https://open-meteo.com/) and map them directly to `state.target.wind` and `state.target.rain`.
* **Adjust Color Palettes:** Edit `clearDeep`, `clearAccent`, `stormDeep`, and `stormAccent` inside `main()` of the fragment shader to create custom themes (e.g., *Aurora Borealis*, *Desert Sandstorm*, or *Cherry Blossom Dusk*).
* **Audio Reactivity:** Feed Web Audio API frequency bands into `u_complexity` or `organicWarp` to turn the geometry into a live music visualizer.

---

## 📄 License

Free to use, modify, and experiment with for personal and creative projects.
