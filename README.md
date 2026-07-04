# NEURAL TOKYO

**A city that drives itself — and one car that learns to.**

One HTML file. No build step, no server, no ML library. Open it and a procedurally generated night-Tokyo comes alive: 1,200 vehicles self-organize using real traffic science, and a real neural network — implemented from scratch in ~150 lines of plain JavaScript — learns to drive from raw camera pixels, live, in front of you.

![NEURAL TOKYO](og.png)

## Run it

```bash
# no install. either:
open index.html          # macOS
# or serve it (recommended for fonts):
npx serve .
```

Requires WebGL (any modern browser). Best on desktop.

## The three views

| Key | View | What you're seeing |
|---|---|---|
| `1` | CITY | Aerial view of 1,200 cars flowing through a signal-free grid. Drag the **HUMAN DRIVERS** slider: at 0% traffic is liquid; push it up and phantom jams condense out of nothing — a real emergent phenomenon of the Intelligent Driver Model, not a script. |
| `2` | CHASE | Cinematic follow-cam behind the crimson hero car. |
| `3` | BRAIN | The hero car switches to a free-body physics model and a neural network starts learning to drive it. Left panel shows the net's actual camera input (48×16 grayscale pixels), every neuron's live activation, the imitation loss falling, and the autonomy blend rising. |

## What is honestly real here

- **Traffic**: longitudinal dynamics are the [Intelligent Driver Model](https://en.wikipedia.org/wiki/Intelligent_driver_model) (Treiber et al., 2000) — the standard car-following model in traffic science. Intersections use time-sliced, signal-free arbitration. "Human" drivers differ only by parameters: longer headways, ~0.7 s perception delay, and random brake taps. Phantom jams emerge from the math, exactly as they do on real highways.
- **The neural network**: a 769→48→24→2 MLP (38,186 parameters), forward pass *and* backpropagation hand-written in plain JS. Input is genuinely the pixels of a WebGL render from the car's front bumper (96×32, downsampled to 48×16 grayscale) plus current speed. Output is steering and acceleration.
- **Learning**: behavioral cloning of a classical teacher (pure pursuit + IDM), trained by SGD with momentum on a replay buffer, in the render loop. When the student drifts off lane, the teacher takes over for a moment and the correction becomes new training data — a DAgger-style loop. The takeover counter and "meters since takeover" are real measurements.
- **Not real**: this is a toy homage, not production autonomy. Nobody's driving stack looks like this. It's ALVINN (1989, 30×32 pixels!) reborn in a browser tab — a love letter to the idea that a camera and a network are enough to learn to drive.

## Why this shape

[Turing Inc.](https://tur.ing) is building camera-first, end-to-end autonomous driving for Tokyo — the thesis that driving intelligence should live in the *brain*, not in an ever-taller stack of sensors. This demo is a tribute to that idea at 1/1,000,000 scale: watch a brain, however small, teach itself the road.

## Architecture (single file, ~2,400 lines)

```
CONFIG / UTILS      seeded RNG — the same city every load
CITY                road graph, parcels, merged-geometry buildings,
                    canvas-generated window & neon textures
TRAFFIC             IDM + intersection arbitration + per-driver profiles
NEURAL              typed-array MLP, backprop, replay buffer, DAgger loop
RENDER              Three.js r160, instanced meshes (6 draw calls for all cars),
                    UnrealBloom, height-adaptive fog, fake wet-road streaks
DIRECTOR / HUD      damped camera rig, EN/JA UI, live brain visualization
```

Handy URL params: `?cars=2000` `?human=0.5` `?mode=brain` `?t=60` (sim warm-up seconds), `?shot=overview|street|hero` (fixed cameras for capture).

## Reproduce the trick

The whole "AI learns to drive" pipeline is four small pieces you can lift:

1. render the scene from the agent's POV into a tiny render target;
2. `readRenderTargetPixels` → grayscale Float32Array;
3. a hand-rolled MLP + backprop (~150 lines — see `nnForward` / `nnTrainBatch`);
4. label each frame with a classical controller's output and imitate it, keeping a takeover rule so mistakes generate data.

No TensorFlow.js required. The browser is enough.

## Credits

Designed and built in one session with **Claude** (Anthropic). Traffic model: Treiber, Hennecke & Helbing (2000). Spiritual ancestor: Pomerleau's ALVINN (1989). Visual language influenced by the [Turing Design System](https://turing-design-system-zeta.vercel.app/).

MIT License.
