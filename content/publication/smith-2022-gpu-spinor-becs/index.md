---
title: "GPU-accelerated solutions of the nonlinear Schrödinger equation for simulating 2D spinor BECs"
date: 2022-06-01
authors: ["Benjamin D. Smith", "Logan W. Cooke", "Lindsay J. LeBlanc"]
publication_types: ["journal_article"]
publication: "Computer Physics Communications 275, 108314"
journal: "Computer Physics Communications"
doi: "10.1016/j.cpc.2022.108314"
abstract: "As a first approximation beyond linearity, the nonlinear Schrödinger equation (NLSE) reliably describes a broad class of physical systems. Though numerical solutions of this model are well-established, these methods can be computationally complex. In this paper, we showcase a code development approach, demonstrating how computational time can be significantly reduced with readily available graphics processing unit (GPU) hardware and a straightforward code migration using open-source libraries. This process shows how CPU computations with power-law scaling in computation time with grid size can be made linear using GPUs. As a specific case study, we investigate the Gross-Pitaevskii equation, a specific version of the nonlinear Schrödinger model, as it describes in two dimensions a trapped, interacting, two-component Bose-Einstein condensate (BEC) subject to a spatially dependent interspin coupling, resulting in an analog to a spin-Hall system. This computational approach lets us probe high-resolution spatial features - revealing an interaction-dependent phase transition - all in a reasonable amount of time. Our computational approach is particularly relevant for research groups looking to easily accelerate straightforward numerical simulation of physical phenomena."
links:
  - name: Publisher's Version
    url: "https://doi.org/10.1016/j.cpc.2022.108314"
  - name: arXiv
    url: "https://arxiv.org/abs/2010.15069"
  - name: Source Code (Spinor-GPE)
    url: "https://github.com/ultracoldYEG/spinor-gpe"
tags: ["bose-einstein condensates", "spin-orbit coupling", "gpu computing"]
---
