# pixel-art-meta

Framework for programmatically generating **ultra-high-fidelity, dimensional pixel art** assets inside a React Artifact using an HTML5 Canvas — targeting the visual tier of late-90s arcade titles (Metal Slug / high-end pixel side-scrollers).

This is a **style definition**, not a single asset. Every generated subject inherits the structural and stylistic rules codified in the style guide.

## Core Rules

1. **Component Layering & Depth** — assets are built from overlapping z-index layers (Background → Main Body → Foreground Armor/Details → Specular Highlights/Glows), never as flat single-layer silhouettes.
2. **Hue-Shifted Specular Shading** — no grayscale overlays; shadows shift into deep indigos/plums/rust-browns, highlights into piercing creams/golds/neon cyans/laser reds.
3. **Manual Anti-Aliasing & Contours** — curved shapes are smoothed with intermediate pixel steps to eradicate jagged stairs.
4. **Rust, Rebar & Greebles** — surfaces carry engineered weathering: 1px rivets, dual-pixel vents, hairline scratches, exposed wiring.
5. **Exhaust & Particle Effects** — propulsion/energy uses decaying geometric pixel steps collapsing into scattered trailing embers.

See **[STYLE_GUIDE.md](./STYLE_GUIDE.md)** for the full technical specification.
