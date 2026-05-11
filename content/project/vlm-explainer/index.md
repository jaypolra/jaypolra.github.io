---
title: "VLM Explainer: From Patches to Phrases"
summary: "Causal explainability tools for vision-language model outputs using Grad-CAM, region masking, and perturbation testing."
tags:
  - PyTorch
  - BLIP
  - CLIP
  - Grad-CAM
  - Explainable AI
  - Streamlit
date: "2025-01-01"

links:
  - type: code
    url: https://github.com/jaypolra/vlm-explainer
---

BLIP generates fluent captions but gives no account of why. The question this project answers: do the image regions the model highlights actually cause the caption, or do they just correlate with it?

Built Grad-CAM token attribution to identify which image regions influenced specific caption words. Validated through perturbation testing: masking the dog region changed "a family walking with their dog" to "a family walking on the beach." Causal influence, not correlation, is the standard.

Added CLIP alignment scoring to cross-verify image-text grounding. Interactive Streamlit interface with 2-click region masking and layer-evolution visualization across shallow-to-deep BLIP representations.
