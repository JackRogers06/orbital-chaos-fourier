# Electron Trajectory & Orbital Chaos Analysis

- This project models an electron moving in the electrostatic field of two stationary protons and analyzes its orbital behavior using numerical integration and Fourier analysis.

**Core Simulation (`solve_ivp`)**

- The differential equations of motion for the electron under Coulomb forces are integrated using `solve_ivp`. Tracking position and velocity over time allows us to plot and analyze the electron's trajectory around the two proton centers.

**Fourier Transforms & Frequency Spectra**

Applying a Fourier transform to the electron’s $y$-position time series breaks the motion down into its frequency components:
* **Periodic Orbits:** Display a discrete spectrum with a few sharp, dominating spectral lines.
* **Chaotic Orbits:** Display a broad, continuous spectrum without clear dominating frequencies.

While Fourier transforms technically assume periodic input, this method works well as a practical approximation over the simulation's observation window.

**Quantifying Chaos (0–5 Chaos Index)**
To compare orbits numerically, the `chaos_score_from_sol` function evaluates the trajectory's spectral entropy (flatness) and time-series roughness to produce a normalized **Chaos Index**:

* **Scale:** `0` (strictly periodic) to `5` (highly chaotic).
* **Design Choice:** A 0–5 integer scale was chosen over a 0–1 decimal range so the leading digit immediately communicates the orbital state at a glance.
