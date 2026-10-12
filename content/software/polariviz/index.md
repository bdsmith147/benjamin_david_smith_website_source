---
title: "PolariViz"
date: 2026-06-01
featured: true
authors: ["Benjamin D. Smith"]
publication_types: ["software"]
summary: "What polarization of light does an atom “see”? An interactive app that shows the polarization amplitudes and intensities in an atom's quantization frame for any beam direction, quantization axis, and input polarization."
language: "Python (Dash, Plotly)"
license: "GPLv3+"
links:
  - name: Live App
    url: "https://bdsmith147.github.io/polariviz/"
  - name: Source Code
    url: "https://github.com/bdsmith147/polariviz"
tags: ["laser cooling and trapping", "polarization", "atomic physics"]
---
What polarization of light does an atom "see"? Well, that depends. This might be a simple answer in highly symmetric configurations. But what if directions and polarization are not so ideal? That is the question this app attempts to answer.

PolariViz was created for AMO (atomic, molecular, and optical) students and researchers. It gives full, arbitrary, and interactive control of the light beam and quantization axis geometry, and the input polarization direction in a laboratory frame. The primary result is a visual and numerical display of the polarization amplitudes and intensities in the quantization frame of the atom. It is designed to help researchers more effectively design and implement AMO experiments, especially where optical access is limited.

The app has four panels:

- **3D lab visualization** of the quantization axis, beam input direction, and input polarization frame.
- **Geometry and polarization control**: beam direction from three Euler angles, quantization axis from polar and azimuthal angles, and input polarization from basic states (H, V, D, A, RHC, LHC) or a quarter-, half-, quarter-wave plate chain.
- **Polarization viewer**: the polarization ellipse, the Poincaré sphere, and the Stokes parameters.
- **Polarization intensities and amplitudes**: a J=0 → J=1 level diagram with the σ₊, π, σ₋ transition intensities, the complex amplitudes, and the coherency matrix in the spherical basis.

The online version runs in any desktop browser. To run it locally, clone the repository, install `dash` and `plotly`, and run `python app.py`.

PolariViz grew out of an earlier PyQt5 tool, the [Polarization Rotation Visualizer](https://github.com/bdsmith147/PolarizationRotationVisualizer).
