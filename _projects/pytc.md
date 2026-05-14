---
layout: page
title: PyTC
description: JAX-based, GPU-accelerated framework for transcorrelated electronic structure methods
importance: 1
category: work
---

**Status:** In active development at Yale (Zhu group), with early-stage development at the Max Planck Institute for Solid State Research (Alavi group). To be released as open source.

## What is PyTC?

PyTC is a high-performance Python framework for **transcorrelated (TC) electronic structure theory**, built on top of the [**JAX**](https://github.com/google/jax) machine-learning framework so that the entire compute pipeline — integral transformation, similarity transformation, and downstream solvers — runs natively on accelerators with `jit` compilation and automatic differentiation.

## Why JAX?

Modern electronic structure code has historically been written in Fortran and C++ with hand-tuned BLAS, which makes it hard to (a) target modern accelerators and (b) compose with the AI-for-science ecosystem. Building PyTC on JAX gives us:

- **Hardware portability without rewriting** — the same code runs on CPU, GPU, and TPU (and any future XLA backend); XLA fuses kernels and matches or beats hand-written CUDA on the workloads that dominate transcorrelation.
- **Composability with neural ansätze.** TC and neural quantum states share a substrate. Putting TC on JAX means TC integrals are differentiable building blocks that downstream NN-based solvers can use directly.
- **Distributed scaling out of the box** via `pmap` / `shard_map`. The infrastructure is built to push *large molecular systems* to multi-accelerator nodes today, with periodic-solid support planned to extend the same machinery toward the thermodynamic limit.

## What's inside

- **Transcorrelated Hamiltonian construction** — one-, two-, and three-body integrals built from the Jastrow-factor similarity transformation, with downstream solver backends for TC-CCSD, TC-DMRG, and TC-FCIQMC-style approaches.
- **Real-space variational Monte Carlo for Jastrow optimization.** The Jastrow parameters that drive the similarity transformation are optimized by sampling electronic configurations from the wavefunction's probability density $\lvert\psi\rvert^2$ and computing stochastic energy gradients. The structure is closely analogous to policy-gradient methods in reinforcement learning: sampled configurations play the role of trajectories, the local energy plays the role of the (negative) reward, and the parameter update is a **variance-reduced stochastic gradient** — obtained by subtracting the mean energy as a baseline, exactly the *REINFORCE-with-baseline* trick used to lower gradient variance in RL. JAX's `vmap` + `grad` make the whole optimizer a few hundred lines of differentiable code that scales across accelerators.
- **Interpolative Separable Density Fitting (ISDF)** — a bedrock numerical primitive for large-scale simulation. ISDF compresses the four-index electron-repulsion tensor into a low-rank factorization, reducing storage from $O(N^4)$ to $O(N^3)$ and dramatically shrinking the prefactor of the $O(N^5)$ contractions that dominate post-mean-field methods. The asymptotic scaling is the same, but the constant gets much smaller — enough to put thousands of basis functions within reach on a single node.
- **Integration hooks for neural-quantum-state solvers** — see [TC-NQS](/projects/tc-nqs/).
- **Periodic-system support — planned.** The integral machinery, density fitting, and distributed primitives are being designed so that the extension to solids and surfaces drops in without re-architecting the framework.

## Why this matters

Transcorrelation accelerates basis-set convergence by an order of magnitude or more, and combined with strong-correlation solvers it brings chemical accuracy to systems that are out of reach of canonical methods. PyTC is engineered to make that capability accessible on commodity accelerator hardware and composable with deep-learning research.

## Related publications

- **Density Matrix Renormalization Group for Transcorrelated Hamiltonians: Ground and Excited States in Molecules** — *J. Chem. Theory Comput.* (2023)
- **Towards Efficient and Accurate Ab Initio Solutions to Periodic Systems via Transcorrelation and Coupled Cluster Theory** — *Phys. Rev. Research* (2021), demonstrated on the uniform electron gas.
