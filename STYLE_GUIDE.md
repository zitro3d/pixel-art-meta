# High-Fidelity 16/32-Bit Pixel Art Style Guide

This document establishes the artistic blueprint and asset pipeline for all programmatically generated sprites and scenes. The goal is a gritty, high-fidelity, dimensional retro-arcade aesthetic (reminiscent of Metal Slug or late-era Neo Geo titles).

## 1. Technical Resolution & Scale

* **Base Target Grid:** Sprites must be drawn using high-density resolution maps relative to their size (e.g., 64x64 for standard characters, 128x64 for light vehicles, 256x128 for heavy objects/tilesets).
* **Sharp Rendering:** Canvas smoothing must be hard-disabled (`ctx.imageSmoothingEnabled = false`). Scale elements using clean integer multipliers to keep pixels perfectly crisp.

## 2. Dimensional Geometry & Contours (The "Anti-Flat" Rule)

To achieve a heavy, 3D, tactile feel instead of flat "programmer art," every asset must adhere to these structural styling laws:

* **Chonky Mechanical Outlines:** Use selective inner dark outlines (deep plum or midnight blue, never pure black) to cleanly separate layered components (e.g., separating a rider from a vehicle, or armor plates from a chassis).
* **Hand-Anti-Aliasing (Hand-AA):** Curved outlines (visors, snouts, tires, vehicle hoods) must use intermediate transitional color pixels on diagonal steps to simulate perfect curves without losing pixel-art integrity.
* **Specular Inset Highlights:** Add a 1-pixel bright highlight line just *inside* the top-facing and forward-facing edges of metallic elements. This gives panels a thick, heavy, stamped-metal appearance.
* **Greebles & Surface Wear:** Flat surfaces are prohibited. Introduce micro-details like 2x1 pixel panel vents, rust scratches, rivets, or exposed wiring to break up large blocks of color.

## 3. Advanced Palette Logic (Hue-Shifting)

* **Dynamic Range Shading:** Do not shade by mixing black or white opacity over base colors.
* **Shadows:** Shift down the color wheel toward cooler, desaturated tones (e.g., yellow metal gets deep rust-brown/olive shadows; skin or pink tones shift into deep plum or indigo shadows).
* **Highlights & Glare:** Shift up toward warm, highly saturated, or fluorescent tones (e.g., cream, blazing yellow, neon cyan, or piercing laser red for visors/thrusters).
