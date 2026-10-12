---
title: "Spinor-GPE"
date: 2021-04-09
authors: ["Benjamin D. Smith", "Logan W. Cooke", "Lindsay J. LeBlanc"]
publication_types: ["software"]
summary: "An open-source Python package for GPU-accelerated solutions to the two-component nonlinear Schrödinger (Gross-Pitaevskii) equation, with applications to spin-orbit coupled Bose-Einstein condensates."
language: "Python (PyTorch)"
links:
  - name: Source Code
    url: "https://github.com/ultracoldYEG/spinor-gpe"
tags: ["bose-einstein condensates", "spin-orbit coupling", "gpu computing"]
---
Spinor-GPE was developed in Professor Lindsay J. LeBlanc's ultracold quantum gases group at the University of Alberta. It solves the two-component Gross-Pitaevskii equation on graphics processing units, which turns simulations that scale as a power law in grid size on a CPU into ones that scale linearly. The method and benchmarks are described in the [companion paper]({{< relref "/publication/smith-2022-gpu-spinor-becs" >}}) in *Computer Physics Communications*.

The package is built on NumPy, with the computational heavy lifting done in PyTorch, which runs on either a conventional processor or a CUDA-enabled NVIDIA graphics card.
