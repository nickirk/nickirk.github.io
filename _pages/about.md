---
layout: about
title: about
permalink: /
subtitle: <a href='https://zhugroup.yale.edu/'>Yale University</a>

profile:
  align: right
  image: prof_pic.jpg
  image_circular: false # crops the image to make it circular
  #more_info: >
  #  <p>555 your office number</p>
  #  <p>123 your address street</p>
  #  <p>Your City, State 12345</p>

news: false # includes a list of news items
selected_papers: false # publications are kept on the dedicated publications page
latest_posts: false # includes a list of latest posts
social: true # includes social icons at the bottom of the page
---

<style>
  .about-intro {
    font-size: 1.05rem;
    line-height: 1.75;
  }

  .about-main {
    clear: both;
    max-width: 52rem;
    margin: 0 auto;
    line-height: 1.72;
  }

  .about-main h2 {
    display: flex;
    align-items: center;
    gap: 0.85rem;
    margin: 2rem 0 1.1rem;
    padding-top: 0.25rem;
  }

  .about-main h2::after {
    content: "";
    height: 1px;
    flex: 1;
    background: var(--global-divider-color);
  }

  .about-main p {
    margin-bottom: 1.35rem;
  }

  .about-main ul {
    margin-bottom: 1.6rem;
    padding-left: 1.25rem;
  }

  .about-main li {
    margin-bottom: 1.05rem;
    padding-left: 0.25rem;
  }

  .about-main li::marker {
    color: var(--global-theme-color);
  }

  .about-role {
    margin-top: 1.75rem;
    padding: 1.15rem 1.25rem;
    border: 1px solid var(--global-divider-color);
    border-left: 3px solid var(--global-theme-color);
    border-radius: 0.35rem;
    background: var(--global-card-bg-color);
  }

  .about-role p:last-child {
    margin-bottom: 0;
  }

  @media (min-width: 768px) {
    .post > article {
      display: grid;
      grid-template-columns: minmax(0, 1fr) minmax(11rem, 26%);
      column-gap: 2rem;
    }

    .post > article > .profile.float-right {
      float: none !important;
      grid-column: 2;
      grid-row: 1;
      align-self: start;
      width: auto;
      margin: 0;
    }

    .post > article > .clearfix {
      display: contents;
    }

    .about-intro {
      grid-column: 1;
      grid-row: 1;
      align-self: center;
    }

    .about-main {
      grid-column: 1 / -1;
      grid-row: 2;
    }

    .post > article > .social {
      grid-column: 1 / -1;
      grid-row: 3;
    }
  }
</style>

<div class="about-intro" markdown="1">

I am a **scientist and ML research engineer building physics-informed AI systems for scientific discovery**. At Yale University, I work with Prof. Tianyu Zhu at the intersection of machine learning, quantum chemistry, and high-performance computing. My goal is to turn expensive, expert-driven scientific analysis into scalable and interpretable computational workflows that connect simulation with experiment.

</div>

<div class="about-main" markdown="1">

## What I build

- **AI that connects spectra to materials properties.** I am developing **AI4ARPES**, a workflow for identifying magnetic phases directly from photoemission spectra. The work combines automated first-principles data generation, physics-informed neural-network classifiers, and domain-adaptation methods for bridging simulated and measured data.
- **GPU software for quantum many-body simulation.** I lead the development of [**PyTC**](/projects/pytc/), a JAX-based framework for transcorrelated electronic-structure calculations. My recent work uses interpolative separable density fitting to compress the transformed Hamiltonian, bringing together numerical linear algebra, JIT-compiled accelerator kernels, and reproducible scientific-software design.
- **Learned representations of correlated electrons.** I combine transcorrelated Hamiltonians with neural quantum states and quantum-embedding methods to build compact models of strongly correlated molecules and materials.

Across research and consulting, I translate scientific questions into computational systems: formulating learning problems, designing data-generation and validation pipelines, implementing models and numerical kernels, and evaluating accuracy and performance. As an external scientific consultant at **ByteDance**, I scoped and evaluated machine-learning research directions for quantum chemistry and advised on algorithmic choices and technical feasibility. My research experience at Yale, Caltech, LMU Munich, and the Max Planck Institute gives me the domain depth to work across ML, physics, and scientific software.

<div class="about-role" markdown="1">

I am actively looking for **Research Scientist, Applied Scientist, and ML Research Engineer roles** in AI for science, scientific machine learning, and accelerated scientific computing. I am especially interested in teams building models and platforms that connect simulation, experiment, and scientific decision-making.

</div>

</div>
