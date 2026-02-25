# macOS Dock in CSS

A faithful recreation of the macOS Dock magnification effect using **pure CSS custom properties** and minimal JavaScript. No frameworks, no build tools — just open the HTML files in a browser.

![macOS Dock in CSS](https://github.com/user-attachments/assets/6d33c856-afb7-435f-8d88-0c82c4fa97fc)

## Live Demos

- **[Dock](https://dashersw.github.io/macos-dock-in-css/dock.html)** — The classic macOS Dock with smooth icon magnification as you hover across it. Icons scale up with a smoothstep curve that mirrors the real Dock's feel.

- **[Time Machine Timeline](https://dashersw.github.io/macos-dock-in-css/time-machine.html)** — The vertical timeline from macOS Time Machine, where date bars expand near the cursor. Same magnification math, applied on the Y axis.

## How the magnification works

The entire magnification pipeline lives in CSS. JavaScript only tracks the mouse position and writes it into a single `--x` (or `--y`) custom property. From there, CSS takes over:

1. **Distance** — each item computes its signed distance from the cursor
2. **Normalize** — the distance is mapped to a `0..1` range based on a configurable `--range`
3. **Smoothstep** — the classic `s²(3 − 2s)` curve replaces a linear falloff with a natural ease-in-out
4. **Scale** — the smoothstep value is multiplied by `--magnification` and added to the base size

This means the animation is frame-perfect and runs on the compositor — no `requestAnimationFrame` loops, no JavaScript layout calculations.

## Settings

Both demos include a settings panel to tweak parameters in real time:

| Parameter      | Dock | Time Machine | Description                                  |
| -------------- | ---- | ------------ | -------------------------------------------- |
| App / Bar size | Yes  | Yes          | Base size of each element                    |
| Magnification  | Yes  | Yes          | How much extra size the closest element gets |
| Range          | Yes  | Yes          | How many neighbors are affected              |
| Gap            | —    | Yes          | Spacing between timeline bars                |
| Position       | Yes  | —            | Move the dock to the right side              |

## Usage

```bash
# Clone the repo
git clone https://github.com/dashersw/macos-dock-in-css.git

# Open either demo in your browser
open dock.html
open time-machine.html
```

No dependencies. No install step.

## License

MIT — Armagan Amcalar
