---
layout: page
title: Embodied Perception & Robot Localization
description: Zero-shot localization, SLAM, and edge AI for autonomous robots
img: assets/img/5.jpg
importance: 5
category: research
authors: "<strong>Dharini Raghavan</strong>, Raghu Krishnapuram, Bharadwaj Amrutur"
venue: "ACM ICVGIP 2024; Qualcomm Developer Symposium"
paper: "https://dl.acm.org/doi/full/10.1145/3702250.3702269"
abstract: "Most SLAM systems quietly assume the same domain at train and test time. We ask what happens when you forbid that assumption: localization must work zero-shot, on a robot the perception model has never seen, in a scene with no fine-tuning. The framework fuses foundation-model visual embeddings with keypoint geometry and spatial consistency constraints, and lifts RTAB-Map accuracy by more than 63% without any task-specific training. Companion work extends the perception stack to differentiable 3D scene representation with anisotropic Gaussian primitives and SE(3) pose refinement, uncertainty-aware multi-robot perception under occlusion, and neural compression for real-time 6-DoF pose estimation on Qualcomm RB5 — 3x speedup at less than 2% accuracy degradation."
---
