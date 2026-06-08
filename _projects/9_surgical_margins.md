---
layout: page
title: Spatial Risk-Field Learning for Surgical Margins
description: Multitask deep learning for breast-cancer margin assessment
img: assets/img/margin.png
importance: 9
category: research
authors: "<strong>Dharini Raghavan</strong>, Anant Madabhushi"
venue: "ARPA-H Collaboration"
abstract: "Surgical margin assessment is usually reported as a single number — positive or negative — but the underlying object is a continuous spatial risk field over tissue geometry. We train a multitask network that learns four coupled views of that field simultaneously: tumor-probability density, signed margin-distance, morphology embedding, and pixel-wise uncertainty. The intermediate network states stop being opaque scores and become interpretable measurements of residual disease risk: surgeons can read off where the model is confident, where it is hedging, and which morphological cues drive the prediction. The framework is built for intraoperative breast-cancer resections in collaboration with ARPA-H, but the structural-prediction-over-geometry formulation generalizes to any margin-assessment task."
---
