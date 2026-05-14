---
layout: page
title: TC-NQS
description: Neural quantum states combined with transcorrelation for strongly correlated systems
importance: 2
category: work
github: https://github.com/nickirk/tc-nqs-preview
---

**Repo:** [nickirk/tc-nqs-preview](https://github.com/nickirk/tc-nqs-preview)

## The idea

[Neural quantum states (NQS)](https://www.science.org/doi/10.1126/science.aag2302) represent a many-body wavefunction by a neural network — typically a restricted Boltzmann machine, transformer, or autoregressive model — and optimize its parameters by stochastic reconfiguration / variational Monte Carlo. NQS is one of the most active frontiers of *AI for science*: the universal-approximation power of deep networks, combined with sampling, can in principle capture wavefunctions of strongly correlated systems that conventional methods struggle with.

**TC-NQS** combines this idea with **transcorrelation**. The transcorrelated (TC) similarity transformation explicitly bakes the electron–electron cusp and other short-range physics into the Hamiltonian, dramatically reducing the variational complexity left for the neural network to learn. The network then specializes in long-range and static correlations — what it is actually good at — while TC handles the singular two-body behaviour that costs NQS most of its expressivity.

## Why it matters for AI4Science

- **TC and NQS are complementary.** The TC similarity transformation removes the electron-electron cusp — the singular short-range structure that any wavefunction ansatz, neural or otherwise, finds hardest to represent. The neural network is then free to specialize in smooth long-range correlations, where deep nets have real expressive power. The two components are doing different jobs, and the combination needs less of each.
- **Better scaling.** NQS on a TC Hamiltonian converges with smaller basis sets, smaller networks, and fewer Monte Carlo samples — directly addressing the wall-clock bottleneck of variational ML for quantum chemistry.
- **A clean testbed for ML methodology.** Quantum many-body Hamiltonians are non-trivial loss landscapes where principled ML choices (architecture, optimizer, sampling) actually matter.

## My role

I conceived the project and supervised its development: defining the methodology, contributing the key algorithmic ideas, and mentoring the Master's student who built the reference implementation.
