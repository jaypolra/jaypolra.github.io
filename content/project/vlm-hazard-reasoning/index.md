---
title: "VLM-Based Hazard Reasoning"
summary: "Domain-aware VLM reasoning for industrial hazard assessment in steel manufacturing environments."
tags:
  - Vision-Language Models
  - Prompt Engineering
  - Industrial AI Safety
  - Explainable AI
date: "2025-01-01"

links:
  - type: code
    url: https://github.com/jaypolra/vlm-hazard-reasoning
---

YOLO can flag a red zone but cannot explain why the scene is dangerous. This project tests whether general-purpose VLMs can fill that explainability gap using structured domain-aware prompting.

Prompts give models physical context about melt shop environments: what pot haulers are, what molten metal implies, what worker corridors mean for safety. Two-stage reasoning pipeline: first describe the scene neutrally, then evaluate against safety conditions.

Output covers scene description, detected entities, spatial relationships, hazard assessment, risk level, and recommended action.
