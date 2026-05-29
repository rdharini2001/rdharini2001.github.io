---
layout: post
title: "Mean Flows for One-Step Generative Modeling"
date: 2026-05-20
description: Tech Talks reading notes — what mean flows are, how they differ from flow matching and consistency models, and why they enable principled one-step generation.
tags: [generative-modeling, flow-matching, diffusion, tech-talks]
categories: tech-talks
giscus_comments: false
related_posts: false
toc:
  beginning: true
---

These are my notes from a recent **Tech Talks** session — the AI journal club I run — on **Mean Flows for One-Step Generative Modeling** by Geng et al. (2025). The paper proposes a clean reformulation of flow-based generative models around an *average velocity field* rather than an *instantaneous* one, and turns one-step generation into a primary, principled training objective rather than a distillation hack.

## The setup: why flow matching, and where it hurts

In standard **flow matching**, we train a network $$v_\theta(x_t, t)$$ to match a target instantaneous velocity field $$u(x_t, t)$$ along an interpolation between data and noise:

$$
\mathcal{L}_{\text{FM}} = \mathbb{E}_{t, x_0, x_1} \Big[\, \big\| v_\theta(x_t, t) - u(x_t, t)\big\|^2 \,\Big]
$$

At inference, we integrate the learned ODE $$\dot{x}_t = v_\theta(x_t, t)$$ from noise to data. The quality of samples depends on how many ODE steps we can afford — more steps reduce discretization error, but cost more.

This creates a tension. Few-step or one-step generation is hugely valuable for deployment, but the model was trained to be an *instantaneous* derivative, not a *finite-displacement* operator. Distillation approaches (consistency models, progressive distillation, rectified flow) try to bridge that gap after the fact.

## The mean-flow idea

The paper's key move is to define and learn the **average velocity**:

$$
\bar{u}(x_t, r, t) \;=\; \frac{1}{t - r}\int_r^t u(x_s, s)\, ds
$$

i.e., the displacement-per-unit-time over a finite interval $$[r, t]$$, rather than the derivative at a single instant. The point: if you have $$\bar{u}$$ exactly, then one Euler step over the whole interval is *exact*:

$$
x_r \;=\; x_t - (t-r)\,\bar{u}(x_t, r, t)
$$

So one-step generation is no longer an approximation — it's the natural inference rule for a model that learned the right object.

## The identity that makes training tractable

The trick is that you can't differentiate through an integral target cheaply. The authors derive a self-referential identity by differentiating the defining equation with respect to $$t$$:

$$
\bar{u}(x_t, r, t) \;=\; u(x_t, t) \;-\; (t - r)\,\frac{d}{dt}\bar{u}(x_t, r, t)
$$

The right-hand side mixes the **instantaneous** velocity (from a standard flow-matching teacher) with a **time-derivative of the mean-flow network itself**. That makes training feasible: you optimize the network to satisfy this consistency identity via JVPs.

This is structurally reminiscent of consistency-model training — both ask a network to satisfy a self-referential invariant — but the invariant here is grounded in calculus, not in a discretization scheme.

## Why I find this interesting

A few reasons it stood out at our journal club:

1. **It reframes one-step generation as the primary object**, not a distillation artifact. The hierarchy "train a continuous model, then distill to a few steps" is replaced by "train the few-step model directly."
2. **It is geometric.** The mean-flow $$\bar{u}(x_t, r, t)$$ is the natural finite-displacement operator along a transport path. This connects to my interest in **flow-based generative geometry** — what do the curvature, density concentration, and asymmetry of transport paths tell us about representation quality?
3. **It hints at a state-modeling reading.** If you think of generative modeling as inferring a latent state and rolling it forward, an instantaneous-velocity model is doing infinitesimal state updates, while a mean-flow model is doing **calibrated finite-horizon predictions** — closer to how world models behave.

## Caveats and open questions

- Training stability with JVP-based self-referential losses is delicate; the paper reports tricks that matter.
- It is unclear (to me) how mean flows interact with **conditional** generation, especially with strong conditioning signals where the velocity changes rapidly near the data manifold.
- The connection to **consistency models** and to **rectified flow** deserves a careful theoretical comparison — they each impose different invariants on the same underlying object.

## Why I wrote this up

I run [Tech Talks](/projects/) as an AI journal club for critical discussion of recent generative-modeling, vision, and medical AI papers. These posts are an attempt to write up sessions in a form useful to others — short, opinionated, and focused on what I think *matters* in the paper rather than reproducing the table of results.

If you'd like to suggest a paper or join a session, [reach out](mailto:draghavan7@gatech.edu).

## References

Geng, Z. et al. (2025). *Mean Flows for One-Step Generative Modeling.* [[arXiv]](https://arxiv.org/abs/2505.13447)
