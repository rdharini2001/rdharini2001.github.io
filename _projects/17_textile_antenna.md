---
layout: page
title: Wearable Textile Antenna Performance Prediction
description: ACO-optimized SVR for wearable textile antenna design
img: assets/img/antenna.png
importance: 17
category: research
authors: "<strong>Dharini Raghavan</strong>"
venue: "IEEE GCITC 2023"
abstract: "Wearable textile antennas are notoriously hard to design — performance depends on substrate weave, conductive thread geometry, body coupling, and bend state, all of which interact non-linearly. We use ant-colony-optimized support vector regression to predict S-parameters and gain across the design space, treating ACO as a hyperparameter and kernel search rather than as the optimizer for the antenna geometry itself. The hybrid surrogate is cheap enough to replace full-wave simulation inside an iterative design loop, and on the held-out designs it generalizes better than grid-search and Bayesian-optimization baselines."
---
