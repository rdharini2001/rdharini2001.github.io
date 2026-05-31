---
layout: page
title: Zero-shot Quality Representation Learning (EyeQC)
description: Learning image-quality representations from frozen vision-language embeddings
img: assets/img/EYQC.png
importance: 1
category: research
authors: "<strong>Dharini Raghavan</strong> et al."
venue: "ARVO 2026 (Hot Topic)"
abstract: "Can image quality be modeled without a single human quality label? EyeQC asks whether the geometry of a frozen vision-language model already encodes acquisition artifacts as latent directions. By contrasting semantic prompt pairs in CLIP-style embedding space, we induce continuous, multi-axis quality directions — blur, illumination shift, contrast loss, occlusion, field-of-view restriction — without supervised quality scores. In retinal imaging the representation supports failure-mode decomposition, retrieval, and batch-shift analysis. We then use quality as both a confounder and a difficulty prior in a curriculum-based visual-acuity regressor, where the model is trained on easy (clean) cases first and gradually exposed to harder (degraded) acquisitions. The resulting BCVA predictor is calibrated under domain shift and outperforms quality-agnostic baselines on out-of-distribution clinic data."
---
