# Pixel Art Standard

The canonical quality bar for every programmatically generated sprite and scene in this repository. Target tier: **late-90s arcade fidelity** (Metal Slug / high-end pixel side-scrollers). Assets are authored on an HTML5 Canvas inside a React artifact, and **every** subject — whatever it is — must satisfy this standard before it ships.

This document is the contract. [`STYLE_GUIDE.md`](./STYLE_GUIDE.md) is the artistic blueprint; this is the enforceable checklist.

---

## 1. Technical Resolution & Scale
- **Logical grid by class:** characters `64×64`, light vehicles `128×64` (or `160×84` working canvas), heavy objects / tilesets `256×128`. Author at logical resolution, never at display resolution.
- **Crisp rendering:** `ctx.imageSmoothingEnabled = false`. Upscale only by **clean integer multipliers**. No sub-pixel scaling, no canvas blur.
- **Compose offscreen:** build the static asset into an offscreen buffer once; animate dynamic layers (particles, glows) on top per frame.

## 2. Component Layering & Depth — the Anti-Flat Rule
- Never draw an asset as a flat, single-layer silhouette.
- Build in explicit **z-index passes**, rear → front:
  `Background / contact shadow → Main Body → Foreground Armor & Details → Specular Highlights & Glows`.
- **Chonky mechanical outlines:** separate layered components with selective inner dark outlines in **deep plum or midnight indigo — never pure black**.
- Finish with a 1px contour around the full silhouette (midnight-indigo) so the asset reads on any background.

## 3. Hue-Shifted Specular Shading
- **Do not** shade by layering black/white opacity over a base color.
- **Shadows** shift *down and cooler* — toward indigo, plum, or warm rust-brown (yellow metal → olive/rust shadow; skin/pink → plum/indigo shadow).
- **Highlights** shift *up and hotter* — toward cream, blazing gold, neon cyan, or piercing laser red (visors, thrusters, glass).
- Define each material as a 5-band ramp: `[specular-hot, highlight, base, shadow, deep-shadow]`.

## 4. Manual Anti-Aliasing & Contours
- All curved edges (helmets, hoods, visors, tires, snouts) get **intermediate transitional pixels** on diagonal steps to eradicate jagged stairs.
- AA color is a hue-shifted mid-tone between the two regions it bridges — never a flat gray.

## 5. Specular Inset Highlights
- Add a **1px bright highlight line just *inside*** the top-facing and forward-facing edges of metallic elements.
- This gives panels a thick, heavy, stamped-metal read.

## 6. Greebles & Surface Wear
- **Flat surfaces are prohibited.** Break up every large color block with micro-detail:
  - 1px rivets, 2×1 panel vents, hairline scratches, exposed wiring clusters, rust pitting, weld seams.

## 7. Exhaust & Particle Effects
- Any mechanical energy or propulsion uses a **dynamic particle system** with **geometric, decaying steps**:
  - Solid glowing neon cores collapse into scattered, trailing 1px embers.
  - Size decays in integer steps (`3 → 2 → 1` px); color decays along the hue-shifted ramp (`cream → cyan → gold → ember-red → out`).
  - Particles interact with the scene (e.g., splay outward on contact with the ground plane).

---

## Ship Checklist
A sprite is done only when **all** of the following are true:

- [ ] Authored at the correct logical grid; integer-scaled; smoothing disabled.
- [ ] Built from ≥3 distinct z-layers, not a flat silhouette.
- [ ] Inner dark outlines (plum/indigo) separate components; full-silhouette contour present.
- [ ] All shading is hue-shifted — zero grayscale overlays, zero pure black.
- [ ] Curved edges are hand-anti-aliased with transitional pixels.
- [ ] Top/forward metal edges carry a 1px specular inset highlight.
- [ ] No flat surfaces — rivets/vents/scratches/wiring present.
- [ ] Any propulsion/energy uses a decaying particle system.

## Reference Implementation
[`hover-bike.html`](./hover-bike.html) — the "Kestrel" hover-bike — is the canonical reference: 9 z-layered passes, per-material hue-shifted ramps, normal-shaded radial engine with manual AA, riveted/vented greebles, exposed copper wiring, and a twin-nozzle decaying particle exhaust.
