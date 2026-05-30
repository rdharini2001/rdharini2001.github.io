---
layout: page
title: Zero-shot Quality Representation Learning (EyeQC)
description: Learning image-quality representations from frozen vision-language embeddings
img: assets/img/EYQC.jpg
importance: 1
category: research
related_publications: true
---

**EyeQC** is a zero-shot method for learning image-quality representations from frozen vision-language embeddings. The framework models acquisition artifacts as latent quality directions induced by semantic prompt contrasts, enabling continuous, multi-axis scoring of blur, illumination shift, contrast loss, occlusion, field-of-view restriction, and other artifacts — without supervised quality labels.

In retinal imaging, this representation supports failure-mode decomposition, retrieval, batch-shift analysis, and quality-aware downstream learning. I extended the method to **curriculum-based visual acuity prediction**, using quality as both a confounder and a difficulty prior for robust regression.

*Presented at ARVO 2026 (Hot Topic).*

### Key ideas
- Quality as latent directions in a frozen VLM embedding space, induced by prompt contrasts.
- Continuous, multi-axis, label-free scoring across acquisition artifacts.
- Quality-aware curriculum for downstream visual acuity regression.
