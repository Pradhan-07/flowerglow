# 🌸 FlowerGlow — Hand Gesture Flower Controller

Control a blooming flower with your hands — in real time, through your webcam. A procedural glowing tulip grows, blooms, and sways on screen as you move your hands. No build step, no install — just open it in a browser.

## ✨ What it does

- **🌷 Procedural glowing tulip** — drawn live on a canvas overlay: a curved stem with leaves, layered petals (3 back + 3 front), stamen and pistil that appear as the flower opens, and 4 side branches with their own mini flowers
- **🤏 Left hand pinch → Bloom** — pinch thumb and index finger together to close the flower, spread them apart to open it
- **🌱 Right hand pinch → Growth** — same pinch gesture with the right hand grows or shrinks the whole plant (stem, leaves, branches)
- **💨 Sway hands → Wind** — moving your hands sideways creates wind that bends the stem and blows the floating pollen particles
- **✨ Floating pollen** — 60 glowing pink particles drift across the screen, pushed by the wind
- **📊 Live HUD** — shows the current Bloom, Grow, and Wind values in the top corner
- **🖐️ Hand skeleton overlay** — a glowing dashed line between thumb and index fingertip with a label ("Left Hand: Bloom" / "Right Hand: Grow")
- **🌿 Natural movement** — layered sine-wave noise keeps the flower swaying gently even when your hands are still; when no hands are detected, the flower slowly closes and shrinks back

## 🖐️ Controls

| Gesture | Effect |
|---|---|
| Left hand pinch (thumb ↔ index finger) | Bloom — 0 (closed) to 1 (fully open) |
| Right hand pinch (thumb ↔ index finger) | Growth — plant grows or shrinks |
| Move hands side to side | Wind — bends the stem and blows pollen |

Pinch is measured as the distance between thumb tip and index fingertip, normalised by hand size (wrist-to-middle-finger distance), so it works at any distance from the camera. The on-screen instructions fade away after 8 seconds.

## 🛠️ Tech stack

- **Vanilla JavaScript** — no framework, no npm dependencies
- **HTML5 Canvas** — all rendering (flower, stem, leaves, particles, HUD)
- **MediaPipe Hands 0.4** — real-time hand tracking (up to 2 hands, `modelComplexity: 1`, detection confidence 0.65, tracking confidence 0.5), loaded from the jsDelivr CDN
- **MediaPipe Camera Utils 0.3** — webcam feed at 1280×720
- **Inter** font from Google Fonts

## ▶️ How to run

No build step — the app is three static files.

1. Clone the repo:
   ```bash
   git clone https://github.com/Pradhan-07/flowerglow.git
   cd flowerglow
   ```
2. Serve it locally (camera access needs a secure context, so `localhost` works but plain `file://` may not):
   ```bash
   python3 -m http.server 8000
   ```
   Then open http://localhost:8000 in your browser.
3. Allow camera access when the browser asks — the loading screen disappears once the camera starts.
4. Hold both hands up in front of the webcam and pinch to bloom and grow the flower.

> Tip: good lighting and a plain background help MediaPipe track your hands reliably.

## 📁 Project structure

```
flowerglow/
├── index.html   # Page layout: webcam video, canvas overlay, loading screen, instructions
├── app.js       # Everything else: hand tracking, flower/stem/petal rendering,
│                #   particles, wind, HUD, animation loop
└── style.css    # Full-screen dark theme, loading animation, instruction toast, vignette
```

## 👤 Author

**Karan Kumar Pradhan** — [Portfolio](https://pradhan.runs-on.dev/)
