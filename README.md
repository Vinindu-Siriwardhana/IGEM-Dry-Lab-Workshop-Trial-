# Wound Patch Lab

An interactive, single-page modelling activity for the HKU iGEM dry-lab workshop (S3–S5 students, 15-minute activity slot). Each student works through 8 unlocking steps and finishes with a patch design the wet lab could test.

**Mission:** a thicker patch holds more bacteria but makes the medicine travel further. How thick should the patch be so the most medicine reaches the wound?

## Run it

Open `index.html` in any modern browser. It has no build dependencies and no external scripts (only Google Fonts, with system-font fallbacks), so it keeps working if the venue wifi drops after loading.

To host it for students, enable **GitHub Pages** (Settings → Pages → Deploy from branch → `main` / root) and share the link or a QR code.

## Steps

| # | Step | Idea students discover |
|---|------|------------------------|
| – | Mission | Scroll-driven story: gas → bacteria → medicine → wound |
| 1 | Sort the cards | Assumptions: only made and lost matter |
| 2 | Medicine sandbox | change = made − lost |
| 3 | Fix the broken model | Lose a share (20%), not a fixed amount — decay rate |
| 4 | Build it step by step | new = old + 12 − 0.2 × old, levels off at 60 |
| 5 | The level in the patch | level = made ÷ 0.2 — steady state |
| 6 | Match the lab data | Fit the loss rate to measurements (≥ 85% match) |
| 7 | Down to the wound | Each layer passes 70% — diffusion, penetration depth |
| 8 | Design the patch | Best thickness is 3 layers (20.6 ≥ 18 to heal) |
| – | Lab Card + Open Lab | Summary of the design, then every setting unlocked |

## Model (illustrative numbers)

| Layers | Made / min | Level in patch | Reaching wound | Heals (≥ 18)? |
|---|---|---|---|---|
| 1 | 4 | 20 | 14.0 | No |
| 2 | 8 | 40 | 19.6 | Yes |
| 3 | 12 | 60 | 20.6 | Yes — best |
| 4 | 16 | 80 | 19.2 | Yes |
| 5 | 20 | 100 | 16.8 | No |

All model maths lives in `Model` in `src/core.js`. Replace the values there with the team's parameters.

## Facilitator notes

- **Helper code:** open any step's Hint → Helper code → `2026`. Completes that step (and any before it) for a stuck student. Change `HELPER_CODE` in `src/core.js`.
- Progress saves in the browser (`localStorage`); **Start over** (tap twice) clears it.
- Works on laptops first; stacks to one column on phones, with the notebook as a pull-up panel.

## Editing

Source is split in `src/`. After editing, rebuild the single page:

```sh
./build.sh
```

| File | Contents |
|---|---|
| `src/style.html` | Title, fonts, all CSS (light + dark themes) |
| `src/markup-1.html` | Header, mission, steps 1–4 |
| `src/markup-2.html` | Steps 5–8, Lab Card, Open Lab, notebook, hint dialog |
| `src/core.js` | Model, state/persistence, notebook, progress, scroll effects, canvas scenes |
| `src/steps-*.js` | Logic for each step, Lab Card, Open Lab, boot |
