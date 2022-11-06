
---
title: 'Gala: A Python package for galactic dynamics'
tags:
  - Julia
  - Quantum Chemical Topology 
  - Interacting Quantum Atoms
  - Cuda.jl
  - Tullio.jl
authors:
  - name: Mario H. Garrido-Czacki
    equal-contrib: true
    affiliation: "1"
  - name: Brandon Meza-González
    equal-contrib: true
    affiliation: "2"
  - name: Tomás Rocha-Rinza
    orcid: 0000-0003-1650-4150
    equal-contrib: true
    affiliation: "2"
  - name: Oscar A. Esquivel-Flores
    orcid: 0000-0003-1451-1285
    equal-contrib: true
    affiliation: "1"
affiliations:
 - name: Instituto de Investigaciones en Matemáticas Aplicadas y en Sistemas, Universidad Nacional Autónoma de México, Circuto Escolar 3000, C.U., Coyoacán, 04510, Ciudad de México, México.
   index: 1
 - name: Instituto de Química, Universidad Nacional Autónoma de México, Circuito Exterior, C. U., Coyoacán, 04510, Ciudad de México, México.
   index: 2
date: 5 November 2022
---

# Summary
`SoftwareName` is a *Quantum Chemical Topology* (QCT) package which computes *critical bound points* (BCP) of the electron charge distribution $\rho(r)$ and determine the stable manifolds of the  BCP of a molecule. Julia programming language[^1] helps to tackle the main bottleneck for the explotation of the *Interacting Quantum Atoms* (IQA) energy partition through calculation of the several integrals in parallel using CUDA.jl package[^2]. `SoftwareName` was created by reverse-engineering the original Fortran code and porting it to Julia in order to harness its support for parallelism, GPU compute, and extensibility.

[^1]: https://julialang.org
[^2]: https://github.com/JuliaGPU/CUDA.jl

# Quantum Chemical Topology

Chemical bonding is one of the most fundamental concepts in chemistry.
The most sound way to examine different sorts of chemical
interactions under the same physical basis is arguably via the examination of
quantum mechanical observables and their expectation values. The electron charge distribution, $\rho(r)$, the pair density, $\rho_2(r_1,
r_2)$, kinetic and potentical energy densities and quantities derived from these functions, e.g., the localisation electron function, the reduced density gradient or the Non-Covalent Index are examples of the above mentionted Dirac observables. The analysis of the local and integrated values of these functions has resulted in the emerging of the field of theoretical computational chemistry known as *Quantum Chemical Topology* (QCT). The origins of QCT are based on the *Quantum Theory of Atoms in Molecules* (QTAIM) which provides a division of the three-dimensional space into basins which are related with the atoms of chemistry envisioned by Dalton at the beginning of the XIX century. These basins are illustrated for the purine molecule $C_{5}H_{4}N_{4}$) in \autoref{qtaim-purine}.

![Trajectories of $\nabla \rho(r)$ of purine computed with the MP2/cc-pVDZ approximation. The basins correspondingto the carbon, hydrogen and nitrogen atoms are shown in black, magenta and blue respectively. The bond and ring critical points ofthe system are displayed as green and red spheres respectively. \label{qtaim-purine}](purina.png){width=80%}

The region comprising any of these basins equals the stable manifold of attractors of the trajectories of $\nabla \rho(r)$, which typically coincide with the position of the nuclei of the system. Such stable manifolds are displayed in black, magenta and blue for the carbon, hydrogen and nitrogen atoms of $C_5H_4N_4$ in Figure \ref{qtaim-purine}. We note that the complete space of purine is exhaustively divided in disjoint regions, the QTAIM-atoms, which are separated by the stable manifold of *Critical Bound Points* (BCP) of $\rho(\mathbf{r})$ shown as small green spheres in Figure \ref{qtaim-purine}. Such separatrices are known as *Inter-Atomic Surfaces* (IAS).
