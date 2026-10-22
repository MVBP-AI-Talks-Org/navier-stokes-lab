# Navier–Stokes Lab — AI-Talks.org

A standalone browser-based interactive fluid dynamics experiment. It evolves an approximate **two-dimensional incompressible Navier–Stokes** flow in a **periodic square domain**. Intended as an educational companion to the AI-Talks.org article *The New Act of Creation: AI, Creativity, and the Future of Science*.

## How to run

Open `index.html` in a modern browser. No build step, server, or dependencies.

## Controls

- **Presets:** double shear layer, Taylor–Green vortex, counter-rotating dipole, four-vortex array, and still water.
- **Viscosity:** kinematic ν controls momentum diffusion.
- **Visualization:** two passive dye channels, signed vorticity, or flow speed.
- **Direct interaction:** pointer stirring injects both dye and force; alternative dye-only/erase brushes.
- **Numerical diagnostics:** mean kinetic energy, RMS vorticity, RMS discrete divergence, elapsed model time, and energy history chart.
- **Export:** PNG screenshot of the fluid field.
- Pause/step/reset; velocity arrows; desktop/mobile responsive.

## Numerical model

The app integrates an approximation to

```
∂u/∂t + (u · ∇)u = −∇p + ν∇²u + f,
∇·u = 0,
```

on a periodic 2D domain using semi-Lagrangian advection, implicit diffusion (8 iterative updates) and a Fourier pressure projection, using the centered-difference divergence symbol. Dye is a passive scalar advected by the evolving velocity field. The scheme is designed for qualitative interactive exploration and exhibits numerical diffusion and projection errors; it is **not** a research-grade CFD code.

For the Taylor–Green flow with zero forcing, the exact velocity amplitude on the normalized unit-periodic square decays as `exp(-8π²νt)`; numerical behavior also contains discretization and interpolation errors.

## Important mathematical limitation

The Clay Millennium Prize question concerns 3D solutions and their potential breakdown under specified conditions. This educational 2D grid calculation cannot detect or rule out a 3D Navier–Stokes singularity, reproduce the 2026 specially forced construction, or prove the Millennium Problem.

## Sources

- [Jos Stam, Stable Fluids (SIGGRAPH 1999)](https://doi.org/10.1145/311535.311548)
- [Clay Mathematics Institute, Navier–Stokes Equation](https://www.claymath.org/millennium/Navier-Stokes-Equation/)
- [Clay Mathematics Institute, September 2026 Announcement](https://www.claymath.org/news/navier-stokes-announcement/)
- [Taylor–Green vortex reference (IIST)](https://www.iist.ac.in/sites/default/files/2025-06/taylor_green.pdf)

## Deploy independently with GitHub Pages

1. Create a new **public** repository named `navier-stokes-lab` under `MVBP-AI-Talks-Org`.
2. Upload `index.html` and optionally `README.md` **to the repository root**.
3. Go to **Settings → Pages → Build and deployment → Deploy from a branch**, select `main` and `/(root)`, then Save.
4. The expected Pages URL is `https://mvbp-ai-talks-org.github.io/navier-stokes-lab/` after Pages publication. This URL is not active until the repository and deployment exist.

No changes to existing Murmuration or Erdős repositories are necessary.