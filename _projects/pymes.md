---
layout: page
title: PyMES
description: Python package for many-electron simulations — coupled-cluster theory for ground states, excited states, and real-time dynamics, with first-class support for non-Hermitian transcorrelated Hamiltonians
importance: 3
category: work
github: https://github.com/nickirk/pymes
---

**Repo:** [nickirk/pymes](https://github.com/nickirk/pymes)

## What it is

PyMES is a **Python package for many-electron simulations** that I have developed and maintained as open source since my PhD years. It implements coupled-cluster theory for both ground and excited states, with first-class support for **non-Hermitian Hamiltonians** — the capability that makes transcorrelated and similarity-transformed methods tractable. It is the reference codebase in which I have developed and validated several published methods, and it continues to be the platform for my work on excited states and real-time electron dynamics.

## What's inside

- **Ground-state coupled cluster** — MP2, CCD, DCD, CCSD, DCSD.
- **Excited states** — EOM-CCSD, FEAST-EOM-CCSD (energy-window targeting), and my own **contour-integral / Cauchy-integral-formula (CIF)** variant that combines black-box eigenvalue targeting with real-time propagation.
- **Real-time electron dynamics** — RT-EOM-CCSD built on the CIF representation of the time-evolution operator. The contour formulation admits much larger time steps than conventional propagators while preserving accurate spectral information ([arXiv:2409.07354](https://arxiv.org/abs/2409.07354)).
- **Non-Hermitian / transcorrelated Hamiltonians as a first-class case.** PyMES treats similarity-transformed Hamiltonians on equal footing throughout — essential for TC methods where conventional Hermitian solvers don't apply directly.
- **Systems.** A 3D uniform electron gas is built in; arbitrary molecules and solids enter via the FCIDUMP interface (read from PySCF or any other electronic-structure package that exports it).
- **Tech stack.** Python, NumPy, SciPy, PySCF, h5py.

## Engineering

- **Tensor-heavy numerical code.** The coupled-cluster contractions that drive every method here are dense numerical linear algebra in Python on top of NumPy/SciPy — broadcasting, memory layout, contraction order, and profiling all matter.
- **A multi-method framework.** Integrals, solvers, and analysis are cleanly separated so that new methods (a new excited-state solver, a new Hamiltonian variant) drop in without disturbing existing ones.
- **Open-source maintainership.** Several hundred commits across multiple contributors, versioned releases, and dependency management.

## Published methods built on PyMES

- The **contour-integral / real-time EOM-CCSD** method — *Liao 2024*, [arXiv:2409.07354](https://arxiv.org/abs/2409.07354).
- **TC-CC** validation on the uniform electron gas — *Liao et al., Phys. Rev. Research* (2021).
