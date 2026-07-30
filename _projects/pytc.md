---
layout: page
title: PyTC
description: JAX-based research framework for transcorrelated electronic-structure methods
importance: 1
category: work
github: https://github.com/nickirk/pytc
---

**Status:** Active research and development at Yale University. The project was initiated and initially developed at the Max Planck Institute for Solid State Research.

**Repo:** [nickirk/pytc](https://github.com/nickirk/pytc)

## What is PyTC?

PyTC is a research framework for **transcorrelated (TC) and explicitly transcorrelated (xTC) electronic-structure methods**. It is built with [JAX](https://github.com/google/jax) so that numerical kernels can use compilation, automatic differentiation, and accelerator backends while remaining accessible from Python.

The project connects transcorrelated Hamiltonian construction with correlated-electron solvers and modern low-rank numerical methods. Its development is guided by reproducible accuracy tests: compressed and accelerated calculations are checked against uncompressed references before performance conclusions are drawn.

The latest manuscript, [**Interpolative Separable Density-Fitting for Transcorrelated Hamiltonians**](https://arxiv.org/abs/2607.17314), presents the ISDF-xTC method implemented in PyTC. It combines low-rank compression of grid-evaluated transcorrelated integrals with multi-GPU execution and automatic differentiation, and applies ISDF-xTC-CCSD to hydrogen chains through cc-pV5Z and benzene with up to 1200 orbitals (cc-pCV5Z).

## Current research directions

- **Low-rank xTC Hamiltonians.** Interpolative separable density fitting (ISDF) compresses the integral tensors that enter xTC calculations. Current validation covers hydrogen chains and large molecular calculations on benzene.
- **Neural quantum states and quantum embedding.** PyTC provides a common numerical foundation for combining transcorrelated Hamiltonians with learned wavefunctions and embedding workflows for correlated materials.
- **Reliable scientific software.** The code emphasizes explicit provenance, numerical diagnostics, CPU/GPU parity checks, and clearly separated reference and accelerated paths.

## Why this matters

Transcorrelation moves difficult short-range correlation effects from the wavefunction representation into a similarity-transformed Hamiltonian. Low-rank factorization and accelerator-friendly implementations can then reduce the storage and computational cost of working with that Hamiltonian. PyTC is designed as a testbed for determining when these ideas deliver accurate, practical gains for molecules and periodic systems.

## Related work

- **Interpolative Separable Density-Fitting for Transcorrelated Hamiltonians** — [arXiv:2607.17314](https://arxiv.org/abs/2607.17314) (2026)
- **Density Matrix Renormalization Group for Transcorrelated Hamiltonians: Ground and Excited States in Molecules** — _Journal of Chemical Theory and Computation_ (2023)
- **Towards Efficient and Accurate Ab Initio Solutions to Periodic Systems via Transcorrelation and Coupled Cluster Theory** — _Physical Review Research_ (2021)
