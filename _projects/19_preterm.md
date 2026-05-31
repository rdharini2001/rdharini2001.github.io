---
layout: page
title: Hybrid Bi-LSTM-Transformer for Preterm-Birth Prediction
description: Temporal gating and self-attention for electrohysterogram signals
img: assets/img/19.jpg
importance: 19
category: research
authors: "<strong>Dharini Raghavan</strong>"
venue: "Biomedical Engineering: Applications, Basis and Communications, 2023"
abstract: "Electrohysterogram (EHG) signals carry information about preterm-labor risk hours before clinical onset, but the signal is multi-channel, low SNR, and dominated by long-range temporal dependencies. We pair a bidirectional LSTM (for temporal gating) with a Transformer (for global self-attention) and add neural-compression layers to keep the model deployable. On the public EHG cohort the hybrid model reaches above 96 percent accuracy with more than 3x inference speedup over the uncompressed baseline. The architectural takeaway: for moderately long biomedical time series, LSTM + attention beats either alone, and the gain comes from short-range gating rather than from the attention layer."
---
